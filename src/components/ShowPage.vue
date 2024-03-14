<script setup>
import {ref} from 'vue';
import {
  Player,
  Audio,
  Ui,
  Controls,
  ControlGroup,
  PlaybackControl,
  VolumeControl,
  CurrentTime, ScrubberControl, EndTime
} from '@vime/vue-next';

const data_1 = [
  {
    title: '野草',
    text: '改编自鲁迅《野草》',
    tag: '摇滚',
    id: '42',
  },
  {
    title: '永不凋落的朝花',
    text: '《朝花夕拾》，经典之作',
    tag: '流行',
    id: '72',
  },
  {
    title: '投枪谣',
    text: '还记得鲁迅先生的《匕首与投枪》吗？',
    tag: '古典',
    id: '53',
  },
  {
    title: '三味回味',
    text: '重温《从百草园到三味书屋》',
    tag: '爵士',
    id: '41',
  },
];
const data_2 = [
  {
    title: 'SHIJING',
    text: '改编自《诗经》',
    tag: '电子',
    id: '11',
  },
  {
    title: '论语摇一摇',
    text: '经典《论语》与流行文化的碰撞',
    tag: '流行',
    id: '16',
  },
  {
    title: '子不语',
    text: '孔老夫子说过什么呢',
    tag: '古典',
    id: '50',
  },
];
const detailVisible = ref(false);
const detailTitle = ref('');
const detailLyrics = ref('');
const detailCover = ref('');
const musicUrl = ref('');

function showDetail(title, id) {
  detailLyrics.value = id + '';
  detailVisible.value = true;
  detailTitle.value = title;
  detailLyrics.value = `车窗外 这夜色 流光溢彩
别忘了 闭上眼 才算醒来
你参演 这场戏 变换姿态
谜底 结局 我该 怎么猜
记忆是梦的开场白
（伤疤被掩盖 昨日还在）
时间在静候你醒来
（Take me away）
别再破碎 别再枯萎
继续沉醉 自我迂回
最后品味 永恒的滋味
下一场那夜的梦 再相会
越是虚伪 越是完美
美梦入睡 绝望轮回
一闭一睁 便开始倒退
下一场那夜的梦 再相会
（伏笔没解开 悬念还在）
时间在静候你醒来
（Sing with me）
别再破碎 别再枯萎
继续沉醉 自我迂回
最后品味 永恒的滋味
来一场不眠之夜 作结尾
越要快乐 越要破溃
是是非非 别再意会
忘记时间 来梦的派对
来一场不眠之夜 作结尾`
  detailCover.value = "https://api.hakush.in/gi/UI/UI_NameCardPic_Gaming_P.webp";
  musicUrl.value = "http://music.163.com/song/media/outer/url?id=2122308127.mp3";
}

</script>
<template>

  <div id="show-container">
    <a-drawer
        destroyOnClose
        :maskStyle="{backgroundImage: 'url(' + detailCover + ')', backgroundSize:'100% 100%', backgroundRepeat: 'no-repeat'}"
        :maskClosable="false"
        v-model:open="detailVisible"
        root-class-name="root-class-name"
        width="100%"
        height="100%"
        style="-webkit-backdrop-filter: blur(40px);backdrop-filter: blur(40px);background-color: hsla(0, 0%, 100%, .8) !important;"
        :title="detailTitle"
        placement="bottom"
    >
      <div id="show-drawer">
        <div id="show-cover-container">
          <img id="cover" width="400" height="348" :src="detailCover" style="object-fit: cover;"/>
          <Player autoplay theme="light" loop id="player">
            <Audio>
              <source :src=musicUrl type="audio/mpeg">
              抱歉，您的浏览器不支持音频播放，请换用最新版火狐浏览器！
            </Audio>
            <Ui>
              <Controls>
                <ControlGroup style="align-items: center;">
                  <PlaybackControl hideTooltip/>
                  <VolumeControl hideTooltip/>
                  <CurrentTime/>
                  <ScrubberControl style="height: 100%"/>
                  <EndTime style="margin-right: 10px"/>
                </ControlGroup>
              </Controls>
            </Ui>
          </Player>
        </div>
        <p id="detail-lyrics">{{ detailLyrics }}</p>
      </div>

    </a-drawer>
    <a-typography-title style="margin-top: 60px;">留声典藏</a-typography-title>
    <a-carousel autoplay>
      <div><img class="show-img" src="https://api.hakush.in/gi/UI/UI_NameCardPic_Neuvillette_P.webp"></div>
      <div><img class="show-img" src="https://api.hakush.in/gi/UI/UI_NameCardPic_Wriothesley_P.webp"></div>
      <div><img class="show-img" src="https://api.hakush.in/gi/UI/UI_NameCardPic_Alhatham_P.webp"></div>
      <div><img class="show-img" src="https://api.hakush.in/gi/UI/UI_NameCardPic_Cyno_P.webp"></div>
    </a-carousel>
    <a-typography-title style="margin-top: 60px;">览文溯忆</a-typography-title>
    <a-tabs>
      <a-tab-pane key="1" tab="鲁迅">
        <a-list item-layout="horizontal" :data-source="data_1">
          <template #renderItem="{ item }">
            <a-list-item>
              <a-list-item-meta
                  :description="item.text">
                <template #title>
                  <a @click="showDetail(item.title,item.id);">{{ item.title }}</a>
                  <a-tag style="margin-left: 10px;" color="red">{{ item.tag }}</a-tag>
                </template>
              </a-list-item-meta>
            </a-list-item>
          </template>
        </a-list>
      </a-tab-pane>
      <a-tab-pane key="2" tab="孔子" force-render>
        <a-list item-layout="horizontal" :data-source="data_2">
          <template #renderItem="{ item }">
            <a-list-item>
              <a-list-item-meta
                  :description="item.text">
                <template #title>
                  <a @click="showDetail(item.title,item.id);">{{ item.title }}</a>
                  <a-tag style="margin-left: 10px;" color="red">{{ item.tag }}</a-tag>
                </template>
              </a-list-item-meta>
            </a-list-item>
          </template>
        </a-list>
      </a-tab-pane>
      <a-tab-pane key="3" tab="余华">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="4" tab="庄子">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="5" tab="李白">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="6" tab="杜甫">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="7" tab="瞿秋白">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="8" tab="蒲松龄">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="9" tab="胡适">Content of Tab Pane 3</a-tab-pane>
      <a-tab-pane key="10" tab="苏轼">Content of Tab Pane 3</a-tab-pane>
    </a-tabs>
  </div>
</template>
<style>
@import '@vime/core/themes/default.css';
@import '@vime/core/themes/light.css';

vm-player {
  --vm-player-theme: #bf1103;
}

#player {
  min-width: 400px;
  @media screen and (max-width: 992px) {
    min-width: 70%;
    max-width: 70%;
    width: 70%;
  }
}

#cover {
  @media screen and (max-width: 992px) {
    display: none;
  }
}

#show-cover-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  @media screen and (max-width: 992px) {
    display: block;
  }
}

#detail-lyrics {
  font-size: 24px;
  line-height: 40px;
  max-height: 80%;
  width: 100%;
  overflow: auto;
  @media screen and (max-width: 992px) {
    text-align: center;
  }
}

#show-drawer {
  white-space: pre-wrap;
  display: flex;
  gap: 12%;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  @media screen and (max-width: 992px) {
    flex-direction: column-reverse;
    gap: 1%;
  }
}

.show-img {
  width: 100%;
  height: 30vh;
  object-fit: cover;
}

#show-container {
  width: 100%;
  padding: 0 200px;

  @media screen and (max-width: 992px) {
    padding: 0 20px;
  }
}
</style>