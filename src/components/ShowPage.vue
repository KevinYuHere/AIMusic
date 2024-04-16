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
    title: '将进酒',
    text: '既是《将进酒》一文，也是李太白一生',
    tag: '国风',
    id: '42',
  },
  {
    title: '太太太白',
    text: '经典唐诗与现代音乐的碰撞',
    tag: '流行',
    id: '72',
  },
  {
    title: '蜀道谣',
    text: '还记得李白的《蜀道难》吗？',
    tag: '古典',
    id: '53',
  },
  {
    title: '桃花潭回味',
    text: '重温《赠汪伦》',
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
  detailLyrics.value = `自古多少杰才鹊起又陨落
大浪淘沙金子也迷失于浑浊
世人题诗作赋无非是畏惧逞强
于三位谪仙今日汇聚颖阳
我曾位居廷堂肆意挥笔成章
每一句诗都引得世人费力争抢
那力士也要为我脱靴退避锋芒
我绣口一吐便是半个瑰丽盛唐
好了不谈故事莫论是与非
来岑夫子我先来提一杯
丹丘生咱们今日登高眺望落日余晖照亮
满桌美酒佳肴务必一醉
那仕途朝纲吵嚷让人脑涨
君子之交往最为宝藏可比皇恩浩荡
天生我材入宫攀援还得非作情
不若挥毫泼墨将进酒杯莫停
君不见黄河之水天上来奔流到海不复回
君不见高堂明镜悲白发朝如青丝暮成雪
接下来的是我的几句醉话
大家不必当真就当我已经睡下
饮酒作乐明月高悬我在山巅挥洒
岁月那汉皇你真的夜能寐吗
我观那潮起明暗间风云变幻
雕砌的盛世之下封酝奸乱
满座文武无人敢说无人反驳
那结局伴随着羞花倾心宣判
我笔走龙蛇百篇诗换不得一隅
赐金我与江山于你皆不过敝履
撕开诬造之谗亦如蜀道之难
徒劳侈谈但愿长醉待后人记叙
对我醉你醉你醉你亦醉
那日排我出京赐金你醉的奇伟
待五花马千金裘呼儿将出换美酒
我便与尔同销万古愁
君不见黄河之水天上来奔流到海不复回
君不见高堂明镜悲白发朝如青丝暮成雪
我笔走龙蛇百篇诗换不得一隅
赐金我与江山于你皆不过敝履
撕开诬造之谗亦如蜀道之难
徒劳侈谈但愿长醉待后人记叙
我醉你醉你醉你亦醉
那日排我出京赐金你醉的奇伟
待五花马千金裘呼儿将出换美酒
我便与尔同销万古愁
君不见黄河之水天上来奔流到海不复回
君不见高堂明镜悲白发朝如青丝暮成雪`
  detailCover.value = "http://p2.music.126.net/RTJkxjQneTlM_XW8vwQ3LQ==/109951168970276948.jpg";
  musicUrl.value = "http://music.163.com/song/media/outer/url?id=2088789466.mp3";
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
      <div><img class="show-img" src="https://www.dpm.org.cn/Uploads/Picture/2024/03/27/s660374644c7ad.jpg"></div>
      <div><img class="show-img" src="https://www.dpm.org.cn/Uploads/Picture/2024/02/29/s65dfe55d35dbc.jpg"></div>
      <div><img class="show-img" src="https://www.dpm.org.cn/Uploads/Picture/2023/12/26/s658a871ca9f08.jpg"></div>
      <div><img class="show-img" src="https://www.dpm.org.cn/Uploads/Picture/2023/08/30/s64eedf76d4e95.jpg"></div>
    </a-carousel>
    <a-typography-title style="margin-top: 60px;">览文溯忆</a-typography-title>
    <a-tabs>
      <a-tab-pane key="1" tab="李白">
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
      <a-tab-pane key="3" tab="余华">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="4" tab="庄子">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="5" tab="王阳明">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="6" tab="杜甫">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="7" tab="瞿秋白">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="8" tab="蒲松龄">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="9" tab="胡适">歌曲精选中，敬请期待</a-tab-pane>
      <a-tab-pane key="10" tab="苏轼">歌曲精选中，敬请期待</a-tab-pane>
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