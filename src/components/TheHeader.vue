<script setup>
import ToggleMode from "@/components/ToggleMode.vue";
import { ref } from 'vue';
</script>
<template>
  <header class="header d-flex justify-between align-center shadow z-10 fixed w-full ">
    <router-link :to="{ name: 'TheHome'}" class="logo d-flex align-center cursor-pointer pl-2">
      <img alt="Vue logo" src="@/assets/img/logo.png" width="45" height="45" />
      <p class="text-lg text-my-green ml-1 font-semibold">GREEN POINT</p>
    </router-link>
    <div id="nav" class="link d-flex align-center justify-around">
      <router-link
          class="font-semibold hover:border-b-4 hover:border-b-my-dark-green border-b-4 border-transparent py-5 px-8 hover:text-pink-400"
          :to="{ name: 'TheHome'}"
      >
        {{ $t('home') }}
      </router-link>
      <router-link
          class="fast-link font-semibold hover:border-b-4 hover:border-b-my-yellow border-b-4 border-transparent py-5 px-8 hover:text-green-400"
          :to="{ name: 'TrashSeparation'}"
      >
        {{ $t('trash-separation') }}
      </router-link>
      <router-link
            :class="dropdownActive ? 'border-b-my-dark-green text-my-dark-green' : '' "
            class="dropdown-main font-semibold hover:border-b-4 hover:border-b-my-dark-green border-b-4 border-transparent py-5 px-8 hover:text-green-400"
            :to="{ name: 'RecyclingCycle'}"
        >
          {{ $t('recycling-cycle') }}

        </router-link>
      <router-link
          class="font-semibold hover:border-b-4 hover:border-b-my-yellow border-b-4 border-transparent py-5 px-8 hover:text-yellow-400"
          :to="{ name: 'TheNews'}"
      >
        {{ $t('health') }}
      </router-link>
      <router-link
          class="font-semibold hover:border-b-4 hover:border-b-my-dark-green border-b-4 border-transparent py-5 px-8 hover:text-blue-500"
          :to="{ name: 'EnvironmentalProtection'}"
      >
        {{ $t('environmental-protection') }}
      </router-link>
      <router-link
          class="font-semibold hover:border-b-4 hover:border-b-my-yellow border-b-4 border-transparent py-5 px-8 hover:text-red-500 "
          :to="{ name: 'TheContact'}"
      >
        {{ $t('contact') }}
      </router-link>
    </div>
    <div class="language d-flex align-center mr-2">
      <ToggleMode class="toggle pr-8 pt-2"/>
      <button class="lang px-3 hover:text-my-dark-green" @click="$i18n.locale = `en`">EN</button>|
      <button class="lang px-3 hover:text-my-dark-green" @click="$i18n.locale = `de`">DE</button>|
      <button class="lang px-3 hover:text-my-dark-green" @click="$i18n.locale = `ua`">UA</button>
    </div>
    <button class="menu-burger" onclick="this.classList.toggle('opened');this.setAttribute('aria-expanded', this.classList.contains('opened'))" aria-label="Main Menu">
      <svg width="50" height="50" viewBox="0 0 100 100">
        <path class="line line1" d="M 20,29.000046 H 80.000231 C 80.000231,29.000046 94.498839,28.817352 94.532987,66.711331 94.543142,77.980673 90.966081,81.670246 85.259173,81.668997 79.552261,81.667751 75.000211,74.999942 75.000211,74.999942 L 25.000021,25.000058" />
        <path class="line line2" d="M 20,50 H 80" />
        <path class="line line3" d="M 20,70.999954 H 80.000231 C 80.000231,70.999954 94.498839,71.182648 94.532987,33.288669 94.543142,22.019327 90.966081,18.329754 85.259173,18.331003 79.552261,18.332249 75.000211,25.000058 75.000211,25.000058 L 25.000021,74.999942" />
      </svg>
    </button>
  </header>
</template>

<style scoped lang="scss">
header {
  .body--dark & {
    background-color: #151515;
    color: white;
    border-bottom: 1px white solid;

    .line {
      stroke: #ffffff;
    };
  }
  .body--light & {
    background-color: white;
  }
}
#nav a.router-link-exact-active:nth-child(2n) {
  color: #d1cc21;
  border-bottom: #fff61a 4px solid;
}
#nav a.router-link-exact-active:nth-child(2n + 1) {
  color: #058240;
  border-bottom: #058240 4px solid;
}

.menu-burger {
  margin-right: 20px;
  display: none;
  background-color: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  width: 30px;
}
.line {
  fill: none;
  stroke: black;
  stroke-width: 4;
  transition: stroke-dasharray 600ms cubic-bezier(0.4, 0, 0.2, 1),
  stroke-dashoffset 600ms cubic-bezier(0.4, 0, 0.2, 1);
}
.line1 {
  stroke-dasharray: 60 207;
  stroke-width: 4;
}
.line2 {
  stroke-dasharray: 60 60;
  stroke-width: 4;
}
.line3 {
  stroke-dasharray: 60 207;
  stroke-width: 4;
}
.opened .line1 {
  stroke-dasharray: 90 207;
  stroke-dashoffset: -134;
  stroke-width: 4;
}
.opened .line2 {
  stroke-dasharray: 1 60;
  stroke-dashoffset: -30;
  stroke-width: 4;
}
.opened .line3 {
  stroke-dasharray: 90 207;
  stroke-dashoffset: -134;
  stroke-width: 4;
}


@media (max-width:1024px) {
  .header {
    .logo {
      p {
        font-size: 10px;
      }
      img {
        width: 30px;
      }
    }
    .link {
      width: 50%;
      a {
        padding: 12px 20px !important;
        font-size: 12px;
      }
    }
    .toggle {
      width: 50px ;
    }
    button {
      font-size: 13px !important;
    }
  }
}
@media (max-width: 768px) {
  .header {
    .menu-burger {
      display: flex;
    }
    .link {
      display: none !important;
    }
  }
}
@media (max-width: 481px) {
  .header {
    width: 100% !important;
    height: 15vh;
    .logo {
      p {
        font-size: 20px;
      }
      img {
        width: 40px;
      }
    }
    .language {
      width: 40%;
      .toggle {
        width: 80px;
      }
      .lang {
        font-size: 20px !important;
      }
    }
    .menu-burger {
      width: 60px;
    }
  }
}
@media (max-width: 320px) {
  .header {
    width: 100% !important;
    height: 15vh;
    .logo {
      margin-right: 150px;
      p {
        font-size: 25px;
      }
      img {
        width: 45px;
      }
    }
    .language {

      .lang {
        font-size: 30px !important;
      }
    }
  }
}
</style>

