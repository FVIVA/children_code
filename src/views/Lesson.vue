<template>
    <div id="lesson">
        <div class="hotLesson">
        <p>热门课程</p>
        <img v-for="(item,index) in hotCourse" :key="index" :src="item.src" @click="item.url">
        </div>
        <div class="allCourse">
            <p>全部课程</p>
            <ul>
               <li v-for="(item,index) in courseList" :key="index" class="courseBtn" 
               :class="{checked:index==nowIndex}" @click="isSelect(index)">{{item.title}}</li>
            </ul>
        </div>
        <div class="course">
            <div v-if="courseIndex==1">Scratch</div>
            <div v-if="courseIndex==2">机器人</div>
            <div v-if="courseIndex==3">人工智能</div>
        </div>
    </div>
</template>
<script>
export default {
  name: "Lesson",
  data() {
    return {
      hotCourse: [
        {
          src: "http://dummyimage.com/300x200/ffe599",
          url: "#"
        },
        {
          src: "http://dummyimage.com/300x200/dd7e6b",
          url: "#"
        },
        {
          src: "http://dummyimage.com/300x200/b6d7a8",
          url: "#"
        }
      ],
      courseList: [
        { title: "Scratch" },
        { title: "机器人" },
        { title: "人工智能" }
      ],
      nowIndex: 0,
      courseIndex: -1
    };
  },
  methods: {
    isSelect(index) {
      this.nowIndex = index;
      this.courseIndex = index + 1;
    }
  },
  mounted() {}
};
</script>
<style lang="less">
#lesson {
  width: 1000px;
  margin: 0 auto;
  p {
    font-size: 20px;
    text-align: center;
    margin-bottom: 35px;
  }
  .hotLesson {
    height: 300px;
    text-align: center;
    img {
      display: inline-block;
      margin-left: 20px;
    }
  }
  .allCourse {
    ul {
      text-align: center;
      .courseBtn {
        display: inline-block;
        padding: 6px 12px;
        font-size: 16px;
        font-weight: 400;
        border: 1px solid transparent;
        border-radius: 4px;
      }
    }
  }
  .course {
      margin-top: 20px;
    div {
      border: 1px solid #ccc;
      border-radius: 4px;
      background-color: #fff;
      width: 1000px;
      height: 200px;
      display: inline-block;
    }
  }
}
.checked {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
</style>
