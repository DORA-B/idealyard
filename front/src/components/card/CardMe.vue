<template>
  <el-card>
    <div class="me-author-name">
      <h1>{{ profile.username }}</h1>
      <p class="slogan-declare" align="center">
        <span style="font-size:16px"><i class="iconfont icon-heart-fill icon-m-right"></i>{{ profile.slogan }}</span>
      </p>
    </div>
    <el-divider></el-divider>
    <div class="profile-detail">
      <span><i class="iconfont icon-location icon-m-right"></i>{{ profile.location }}</span>
      &nbsp;
      <span><i class="iconfont icon-company icon-m-right"></i>{{profile.company }}</span>
      &nbsp;
      <span><i class="iconfont icon-idcard icon-m-right"></i>{{profile.occupation }}</span>
    </div>

    <div class="profile-detail">
      <i @click="showTool(qq)" :title="qq.title" class="iconfont icon-QQ"></i>
      <i @click="showTool(github)" :title="github.title" class="iconfont icon-github-fill"></i>
      <i @click="showTool(bilibili)" :title="bilibili.title" class="iconfont icon-movie"></i>
      <i @click="showTool(zhihu)" :title="zhihu.title" class="iconfont icon-zhihu"></i>
      <i @click="showTool(email)" :title="email.title" class="iconfont icon-mail"></i>
    </div>
  </el-card>

</template>

<script>
  import {isUrl} from '@/utils/regexr'

  export default {
    name: 'CardMe',
    data() {
      return {
        profile: {
          'username': '庯茳伍德',
          'slogan': '两个大力士',
          'location': 'China',
          'company': '讲武堂',
          'occupation': '大师',
        },
        qq: {title: 'QQ', message: 'Call him!'},
        github: {
          title: 'Github',
          message: 'https://github.com/DORA-B'
        },
        bilibili: {
          title: 'Bilibili',
          message: 'https://space.bilibili.com/354657020'
        },
        zhihu: {
          title: 'Zhihu',
          message: 'https://www.zhihu.com/people/DORA'
        },
        email: {
          title: 'Email',
          message: '2358543632@qq.com'
        }
      }
    },
    methods: {
      showTool(testData) {
        // 如果是链接则跳转，如果是string则显示
        const testStr = testData.message
        if (isUrl(testStr)) {
          window.open(testStr)
        } else {
          const _title = testData.title
          this.$message.info({
            title: _title,
            position: 'top-right',
            dangerouslyUseHTMLString: true,
            message: '<strong>' + testStr + '</strong>',
            duration: 2000,
            offset: 150
          });
        }
      }
    }
  }
</script>

<style scoped>
  .me-author-name {
    text-align: center;
    font-size: 30px;
    /*border-bottom: 1px solid #5FB878;*/
  }

  .el-divider {
    background-color: #5FB878;
  }

  .profile-detail {
    text-align: center;
    padding-top: 10px;
    font-size: 15px;
  }

  .profile-detail > i {
    cursor: pointer;
    padding: 4px 10px;
    font-size: 20px;
  }
</style>
