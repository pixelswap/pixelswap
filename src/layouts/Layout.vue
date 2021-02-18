<template>
  <div class="nescss">
    <pixel-header v-bind:scroll-pos="scrollPos" v-bind:is-active="isActive"
                      v-bind:rtx-balance="acountInfo.rtxBalance"
                      v-bind:wallet-address="acountInfo.walletAddress"></pixel-header>
    <div class="container">
      <button type="button" class="nes-btn is-error scroll-btn" v-bind:class="{active: !isActive}"
              v-on:click="scrollToTop()"><span>&lt;</span></button>
      <pixel-content v-bind:is-active="isActive"></pixel-content>
    </div>
    <pixel-footer></pixel-footer>
  </div>
</template>

<script>
  import PixelHeader from 'components/PixelHeader.vue'
  import PixelFooter from 'components/PixelFooter.vue'
  import PixelContent from 'components/PixelContent.vue'

  export default {
    name: 'Layout',
    components: {
      PixelHeader,
      PixelFooter,
      PixelContent
    },
    data () {
      return {
        scrollPos: 0,
        isActive: true,
        acountInfo: {
          rtxBalance: 0,
          walletAddress: ''
        }
      }
    },
    async mounted () {
      document.addEventListener('scroll', () => {
        this.scrollPos = document.documentElement.scrollTop || document.body.scrollTop
        this.isActive = this.scrollPos <= window.outerHeight * 0.3
      })
      this.waitTronInit().then()
    },
    methods: {
      scrollToTop: function () {
        window.scrollTo({
          left: 0,
          top: 0,
          behavior: 'smooth'
        })
      },
      waitTronInit: async function () {
        // 1. check variable, 检查tronweb是否已经加载
        if (window.tronWeb) {
          const tronWeb = window.tronWeb
          // 2. check node connection，检查所需要的API是否都可以连通
          const nodes = await tronWeb.isConnected()
          const connected = !Object.entries(nodes).map(([name, connected]) => {
            if (!connected) {
              console.error(`Error: ${name} is not connected`)
            }
            return connected
          }).includes(false)
          if (connected) {
            // 3. 已加载tronLink，获取账户余额。
            if (window.tronWeb && window.tronWeb.defaultAddress.base58) {
              // 已加载tronLink
              this.acountInfo.walletAddress = window.tronWeb.defaultAddress.base58
              this.acountInfo.rtxBalance = await tronWeb.trx.getBalance(window.tronWeb.defaultAddress.base58)
              console.log('当钱包TRX余额：' + this.acountInfo.rtxBalance / 1e6)
            }
          } else {
            console.error('Error: TRON node is not connected')
            console.error('wait for tronLink')
            setTimeout(async () => {
              await this.waitTronInit()
            }, 100)
          }
        } else {
          // 如果检测到没有注入tronWeb对象，则等待100ms后重新检测
          console.error('waiting for tronLink')
          setTimeout(async () => {
            await this.waitTronInit()
          }, 100)
        }
      }
    }
  }
</script>
<style>
  .container {
    padding-top: constant(safe-area-inset-top);
    padding-top: env(safe-area-inset-top);
    /*padding-bottom: constant(safe-area-inset-bottom);*/
    /*padding-bottom: env(safe-area-inset-bottom);*/
    /*padding-left: constant(safe-area-inset-left);*/
    /*padding-left: env(safe-area-inset-left);*/
    /*padding-right: constant(safe-area-inset-right);*/
    /*padding-right: env(safe-area-inset-right);*/
  }
</style>
