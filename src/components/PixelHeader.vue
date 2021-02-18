<template>
  <header v-bind:class="{sticky: !isActive}">
    <div class="container">
      <div class="nav-btn" v-on:click="navbarTraggle()">
        <q-btn flat round dense icon="menu" class="q-mr-xs">
        </q-btn>
      </div>
      <div class="nav-brand">
        <a href="#">
          <div class="logo">
<!--            <i class="snes-jp-logo brand-logo"></i>-->
            <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="50px" height="50px" viewBox="0 0 50 50" enable-background="new 0 0 50 50" xml:space="preserve">
              <image width="50" height="50" x="0" y="0" href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGlkPSLlm77lsYJfMSIgZGF0YS1uYW1lPSLlm77lsYIgMSIgdmlld0JveD0iLTMgMCA0NyA1MCI+PGRlZnM+PHN0eWxlPi5jZC1zdmctbG9nby1ibHVlLTF7ZmlsbDojMjM3NWY5O30uY2Qtc3ZnLWxvZ28tYmx1ZS0ye2ZpbGw6I0ZGMDA2Njt9LmNkLXN2Zy1sb2dvLWJsdWUtM3tmaWxsOiMxODZkZWE7fTwvc3R5bGU+PC9kZWZzPjx0aXRsZT5sb2dvPC90aXRsZT48cGF0aCBjbGFzcz0iY2Qtc3ZnLWxvZ28tYmx1ZS0xIiBkPSJNMzkuOCwyMi4zbC02LjYtOC42LS4zLS4zYTIuNSwyLjUsMCwwLDAtMS43LS45TDI3LjcsMTJhMi42LDIuNiwwLDAsMC0xLjkuNUwxMCwyNC45YTIuMywyLjMsMCwwLDAtLjQsMy4ybC41LjZhMi4zLDIuMywwLDAsMCwzLjIuNEwyOC4yLDE3LjZhMi4zLDIuMywwLDAsMSwzLjIuNGwzLjUsNC41YTIuMywyLjMsMCwwLDEtLjQsMy4yTDE2LDQwYTEuNCwxLjQsMCwwLDAtLjMsMS45aDBsNC42LDUuOWEuNi42LDAsMCwwLDEtLjJsMS43LTUuNC4zLS4yTDM5LDI5LjhhMi45LDIuOSwwLDAsMCwxLjEtMmwuNC0zLjJBMy4yLDMuMiwwLDAsMCwzOS44LDIyLjNaIi8+PHBhdGggY2xhc3M9ImNkLXN2Zy1sb2dvLWJsdWUtMiIgZD0iTTMyLjIsMjIuMSwzMSwyMC41YTEuNywxLjcsMCwwLDAtMi40LS4zTDEyLjgsMzIuNmExLjcsMS43LDAsMCwxLTIuNC0uM0w2LjIsMjYuOWExLjcsMS43LDAsMCwxLC4zLTIuNEwyNS40LDkuOGExLjMsMS4zLDAsMCwwLC41LS43LDEsMSwwLDAsMC0uMS0uOS45LjksMCwwLDAtLjYtLjRoMGwtNS41LS40YTIuNCwyLjQsMCwwLDAtMS43LjVMMi40LDIwYTIuOCwyLjgsMCwwLDAtMS4xLDEuOUwxLDI1LjNhMi45LDIuOSwwLDAsMCwuNiwyLjFsNi43LDguNy40LjVhMS45LDEuOSwwLDAsMCwxLjMuN2w0LC40YTIsMiwwLDAsMCwxLjQtLjRMMzEuOSwyNC41QTEuNywxLjcsMCwwLDAsMzIuMiwyMi4xWiIvPjxyZWN0IGNsYXNzPSJjZC1zdmctbG9nby1ibHVlLTIiIHg9IjIzLjMiIHk9IjUuOCIgd2lkdGg9IjEuMiIgaGVpZ2h0PSIxLjIzIiByeD0iMC4yIiByeT0iMC4yIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNCAtMTYuMykgcm90YXRlKDUxLjUpIi8+PHJlY3QgY2xhc3M9ImNkLXN2Zy1sb2dvLWJsdWUtMiIgeD0iMjAuMSIgeT0iNS43IiB3aWR0aD0iMS40IiBoZWlnaHQ9IjEuMzciIHJ4PSIwLjIiIHJ5PSIwLjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEyLjggLTEzLjgpIHJvdGF0ZSg1MS41KSIvPjxyZWN0IGNsYXNzPSJjZC1zdmctbG9nby1ibHVlLTIiIHg9IjI2LjIiIHk9IjYuMyIgd2lkdGg9IjEiIGhlaWdodD0iMC45OCIgcng9IjAuMiIgcnk9IjAuMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTUuMyAtMTguMykgcm90YXRlKDUxLjUpIi8+PHJlY3QgY2xhc3M9ImNkLXN2Zy1sb2dvLWJsdWUtMiIgeD0iMjUuMiIgeT0iNC41IiB3aWR0aD0iMC45IiBoZWlnaHQ9IjAuODYiIHJ4PSIwLjIiIHJ5PSIwLjIiIHRyYW5zZm9ybT0ibWF0cml4KDAuNjIsIDAuNzgsIC0wLjc4LCAwLjYyLCAxMy41MywgLTE4LjE2KSIvPjxyZWN0IGNsYXNzPSJjZC1zdmctbG9nby1ibHVlLTIiIHg9IjIyLjIiIHk9IjQuMyIgd2lkdGg9IjEiIGhlaWdodD0iMS4wMyIgcng9IjAuMiIgcnk9IjAuMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTIuMyAtMTYpIHJvdGF0ZSg1MS41KSIvPjxyZWN0IGNsYXNzPSJjZC1zdmctbG9nby1ibHVlLTIiIHg9IjI1LjciIHk9IjIuMSIgd2lkdGg9IjAuNyIgaGVpZ2h0PSIwLjY5IiByeD0iMC4xIiByeT0iMC4xIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMS43IC0xOS40KSByb3RhdGUoNTEuNSkiLz48cmVjdCBjbGFzcz0iY2Qtc3ZnLWxvZ28tYmx1ZS0yIiB4PSIyNC4xIiB5PSIzLjIiIHdpZHRoPSIwLjgiIGhlaWdodD0iMC43OCIgcng9IjAuMSIgcnk9IjAuMSIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTIgLTE3LjgpIHJvdGF0ZSg1MS41KSIvPjwvc3ZnPg==" />
            </svg>
            <div>
              <h2>PixelSwap</h2>
              <p>heco defi project.</p>
            </div>
          </div>
        </a>
      </div>
<!--      <div class="nav-menu">-->
<!--        <span @click="routerToHome()">首页</span>-->
<!--      </div>-->
      <navbar class="navbar-container">
        <ul>
          <li>
            <span @click="routerToHome()"><b>Home</b></span>
          </li>
          <div class="h-sep"></div>
          <li>
            <span @click="routerToHome()">Chats</span>
          </li>
          <li>
            <span @click="routerToHome()">Users</span>
          </li>
          <div class="h-sep"></div>
          <li>
            <span @click="routerToHome()">FAQ</span>
          </li>
          <li>
            <span @click="routerToHome()">Contact</span>
          </li>
          <div class="h-sep"></div>
          <li>
            <span @click="routerToHome()">Login</span>
          </li>
        </ul>
      </navbar>
      <div class="wallet">
        <section>
          <button type="button" class="nes-btn" v-on:click="showWallet()">
            <span v-if="walletAddress">
              {{walletAddress}}
            </span>
            <span v-else>
              <img
                src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA8AAAASCAYAAACEnoQPAAAA0klEQVQ4T7WTsQ6DIBCGDxNTbFf7SK4uHUrSZ+wio8/EViuJiTSHQhAEbNIykeO+///hlMDOqqpK+eVxHIlfCwrXulavYYCu62xv27YwTROUZQmuyAamlCrO+V4YXUMRXEbAwi7YNA0URQHzPFuhvu/1njEGQgjNBTCCbt2JoYyA6dGw75qDMT5G38AJV/SIO0spTcJgAuvBPhx93u1BFA4+igOC+s5KPQ+0ei2XxzKq38LkFibx02WdUSR2pf/CqWfMOqfg0339Mc4Uvp7zWwL5AIJya4I635S+AAAAAElFTkSuQmCC"
                alt="">
              连接钱包
            </span>
          </button>
        </section>
      </div>
    </div>
    <div class="navbar">
      <q-slide-transition>
        <div v-show="isTraggle">
          <q-list>
            <q-item clickable>
              <q-item-section>无限玩法</q-item-section>
            </q-item>
            <q-item clickable>
              <q-item-section>创世兑换</q-item-section>
            </q-item>
            <q-separator></q-separator>
            <q-item clickable>
              <q-item-section>项目规划</q-item-section>
            </q-item>
            <q-item clickable>
              <q-item-section>团队介绍</q-item-section>
            </q-item>
          </q-list>
        </div>
      </q-slide-transition>
    </div>
  </header>
</template>
<script>
    import dialogPolyfill from 'dialog-polyfill'

    export default {
    name: 'PixelHeader',
    props: [
      'scrollPos',
      'isActive',
      'rtxBalance',
      'walletAddress'
    ],
    data () {
      return {
        isTraggle: false
      }
    },
    async mounted () {
      function createDialog (content, options) {
        options = Object.assign({
          modal: true,
          className: '',
          wrap: false
        }, options)

        const dialog = document.createElement('dialog')
        dialogPolyfill.registerDialog(dialog)

        const dialogContent = options.wrap ? document.createElement('div') : dialog
        if (dialogContent !== dialog) {
          dialog.append(dialogContent)
        }

        if (typeof content === 'string') {
          dialogContent.innerHTML = content
        } else {
          dialogContent.append(content)
        }
        if (options.className) {
          dialog.className = options.className
        }
        if (options.id) {
          dialog.id = options.id
        }

        const holder = Object.assign(document.createElement('div'), { className: '' })
        holder.append(dialog)

        document.body.append(holder)
        return dialog
      }
      const dialogInnerHtml = `<form method="dialog">
                                <p class="title">Dialog</p>
                                <p>Alert: this is a dialog.</p>
                                <menu class="dialog-menu">
                                  <button class="nes-btn">Cancel</button>
                                  <button class="nes-btn is-primary">Confirm</button>
                                </menu>
                              </form>`
      createDialog(dialogInnerHtml, {
        className: 'nes-dialog',
        id: 'dialog-default'
      })
    },
    methods: {
      navbarTraggle: function () {
        this.isTraggle = !this.isTraggle
      },
      routerToHome: function () {
        this.$router.push({
          path: '/'
        })
      },
      showWallet: function () {
        var dialog = document.getElementById('dialog-default')
        // Now dialog always acts like a native <dialog>.
        dialog.showModal()
      }
    }
  }
</script>
<style>
  header {
    padding-top: constant(safe-area-inset-top);
    padding-top: env(safe-area-inset-top);
    /*padding-bottom: constant(safe-area-inset-bottom);*/
    /*padding-bottom: env(safe-area-inset-bottom);*/
    /*padding-left: constant(safe-area-inset-left);*/
    /*padding-left: env(safe-area-inset-left);*/
    /*padding-right: constant(safe-area-inset-right);*/
    /*padding-right: env(safe-area-inset-right);*/
  }

  header .q-btn .q-icon, header .q-btn .q-spinner {
    font-size: 2.3em;
  }

  .navbar-container {
    background-color: #ffd700;
    border-radius: 5px;
    display: table;
  }

  .navbar-container ul {
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    /*-webkit-justify-content: space-around;*/
    -ms-flex-pack: distribute;
    /*justify-content: space-around;*/
    border: 2px solid #ffd700;
    border-radius: 5px;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .navbar-container ul li > span {
    display: block;
    padding: 10px 10px;
    margin: 0 5px;
    text-decoration: none;
    border-radius: 3px;
    font-weight: 300;
    color: #212529;
    text-shadow: 0 1px 0 black;
    -webkit-transition: all ease .25s;
    transition: all ease .25s;
  }

  .navbar-container ul li > span:hover {
    background-color: #212529;
    color: #ffd700;
    text-shadow: none;
  }

  .navbar-container ul li:first-child > span {
    margin: 0 5px 0 0;
  }

  .navbar-container ul li:last-child > span {
    margin: 0 0 0 5px;
  }

  .navbar-container ul .h-sep {
    display: block;
    width: 1px;
    background: rgba(250, 235, 215, 0.1);
  }

  @media screen and (max-width: 768px) {
    .navbar-container {
      display: none;
    }
  }
</style>
