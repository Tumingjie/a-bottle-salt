<template>
  <div class="divBase">

    <div ref="backGroundBox" class="box">
      <div class="image-wrap">
        <div class="image" :style="{backgroundImage: `url(${firstImg})`}"></div>
      </div>
    </div>

    <div style="height: 10%;width: 100%;background-color: #0D0D0D;">
      <toolbar></toolbar>
    </div>

    <div style="width: 100%;height: 70%;position: relative">
      <img style="width: 100%;height: 100%;position: absolute" :src="secondImg"/>
    </div>

    <div style="width: 100%;height: 20%;padding: 0 5% 0 5%;">
      <table class="divBase">
        <tr>
          <td style="width: 33%;height: 100%">
            <div style="width: 60%;height: 30%;color: #BAB9B6;font-size: 14px;font-style: italic;">
              PHONE NUMBER：<span style="font-size: 12px;color: #8c939d">{{contacts.phone}}</span>
            </div>
            <div style="width: 60%;height: 70%;color: #8c939d;font-size: 12px;font-style: italic;">
              {{contacts.address}}
            </div>
          </td>
          <td style="width: 33%;height: 100%">
            <div style="width: 60%;height: 30%;color: #BAB9B6;font-size: 14px;font-style: italic;">
              OUR SOCIAL：
            </div>
            <div style="width: 100%;height: 70%;color: #8c939d;font-size: 12px;font-style: italic;">
              <el-tooltip v-for="(item) in contactImages" class="item" effect="dark" :content="item.content" placement="top-start">
                <div style="width: 10%;height: 20%;position: relative;display: inline-block;padding-left: 5%">
                  <img style="position: absolute;width: 75%;height: 100%" :src="item.img"/>
                </div>
              </el-tooltip>
            </div>
          </td>
          <td style="width: 33%;height: 100%">
            <div style="width: 60%;height: 30%;color: #BAB9B6;font-size: 14px;font-style: italic;">
              E-MAIL：
            </div>
            <div style="width: 60%;height: 70%;color: #8c939d;font-size: 12px;font-style: italic;">
              {{contacts.email}}
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
  import toolbar from './components/toolbar'
  import contacts from './components/contacts'

  import boxes from './commonScripts/moveBackground'

  export default {
    name: 'Contacts',
    components: { toolbar, contacts },
    data() {
      return {
        firstImg: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fphoto%2F2009-4-13%2F200904112336058564.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1658928800&t=8913213d93980e32fae1222eda918e7f',
        secondImg: 'https://img1.baidu.com/it/u=3098127009,1379997600&fm=253&fmt=auto&app=138&f=JPEG?w=1179&h=500',
        contacts: {
          id: 1,
          phone: '1866 - 56 -33 -202',
          address: 'ROOM 1109,BUILDING #61,YUANYANGTIANDI,MID RD.EAST 4TH RING,CHAOYANG DISTRICT,BEIJING',
          email: 'SALTSTUDIO@YEAH.NET'
        },
        contactImages: [
          {
            id: 1,
            img: 'require(\'@/assets/images/twitter.jpeg\')',
            content: 'twitter'
          },
          {
            id: 2,
            img: 'require(\'@/assets/images/twitter.jpeg\')',
            content: 'twitter'
          },
          {
            id: 3,
            img: 'require(\'@/assets/images/twitter.jpeg\')',
            content: 'twitter'
          },
        ]
      }
    },
    mounted() {

      //背景图移动起来
      let boxElement = this.$refs.backGroundBox
      boxes.push({
        el: boxElement,
        targetX: 0,
        targetY: 0,
        x: 0,
        y: 0,
        left: boxElement.offsetLeft,
        top: boxElement.offsetTop,
        size: boxElement.offsetWidth
      })
    }
  }
</script>

<style scoped>
  @import './commonCSS/moveBackground.scss';

  .divBase {
    width: 100%;
    height: 100%;
  }

  >>> .el-breadcrumb__inner {
    color: #BDBBB7 !important;
  }

  >>> .el-button--primary {
    color: #FFFFFF;
    background-color: #0D0D0D;
    border-color: #0D0D0D;
  }
</style>
