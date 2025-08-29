<template>
  <div class="text-center mb-6">
    <!-- 公司名称 -->
    <h1 class="enter-x mb-2 text-3xl font-bold text-gray-800 xl:text-4xl">
      华筑智居
    </h1>
    <!-- 标语 -->
    <p class="enter-x mb-4 text-base text-gray-600 xl:text-lg">
      智在生活·用心陪伴
    </p>
    <!-- 分隔线 -->
    <div class="w-16 h-0.5 bg-gradient-to-r from-blue-400 to-purple-500 mx-auto mb-4"></div>
    <!-- 原有标题 -->
    <!-- <h2 class="enter-x text-center text-xl font-semibold text-gray-700 xl:text-2xl">
      {{ getFormTitle }}
    </h2> -->
  </div>
</template>
<script lang="ts" setup>
import { LoginStateEnum, useLoginState } from './useLogin'

defineOptions({ name: 'LoginFormTitle' })

const { t } = useI18n()

const { getLoginState } = useLoginState()

const getFormTitle = computed(() => {
  const titleObj = {
    [LoginStateEnum.RESET_PASSWORD]: t('sys.login.forgetFormTitle'),
    [LoginStateEnum.LOGIN]: t('sys.login.signInFormTitle'),
    [LoginStateEnum.REGISTER]: t('sys.login.signUpFormTitle'),
    [LoginStateEnum.MOBILE]: t('sys.login.mobileSignInFormTitle'),
    [LoginStateEnum.QR_CODE]: t('sys.login.qrSignInFormTitle'),
    [LoginStateEnum.SSO]: t('sys.login.ssoFormTitle')
  }
  return titleObj[unref(getLoginState)]
})
</script>
