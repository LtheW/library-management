<template>
  <!--collapse 是否水平折叠收起菜单-->
  <el-menu    
    :default-active="$route.path"
    router
    unique-opened    
    class="el-menu-vertical-demo"
    background-color="#545c64"
    text-color="#fff"
    active-text-color="#ffd04b"
  >
    <!--是否水平折叠收起菜单 会影响这里字段的显示 -->
    <!-- <h3 v-show="isCollapse">偶囧</h3> -->
    <!-- <h3 v-show="!isCollapse">偶囧后台管理系统</h3> -->
    <el-menu-item :index="item.path" v-for="item in noChildren" :key="item.path" @click="clickMenu(item)">
      <i :class="'el-icon-' + item.icon"></i>
      <span slot="title">{{ item.label }}</span>
    </el-menu-item>
    <el-submenu :index="item.label" v-for="(item, index) in hasChildren" :key="index">
      <template slot="title">
        <i :class="'el-icon-' + item.icon"></i>
        <span slot="title">{{ item.label }}</span>
      </template>
      <el-menu-item-group>
        <el-menu-item :index="subItem.path" v-for="(subItem, subIndex) in item.children" :key="subIndex" @click="clickMenu(subItem)">
          <i :class="'el-icon-' + subItem.icon"></i>
          <span slot="title">{{ subItem.label }}</span>
        </el-menu-item>
      </el-menu-item-group>
    </el-submenu>
  </el-menu>
</template>
 
<script>
export default {  
  //计算属性
  computed: {
    //没有子菜单
    noChildren() {
      return this.menu.filter(item => !item.children)
    },
    //有子菜单 (这样设置会有一个问题 就是有子菜单的 永远会在没有子菜单的下面）
    hasChildren() {
      return this.menu.filter(item => item.children)
    },
    // isCollapse() {
    //   // 这里的数据就是从vuex取得
    //   return this.$store.state.tab.isCollapse
    // }
  },
  data() {
    return {
      menu: [
        {
          path: '/user',
          name: 'user',
          label: '用户管理',
          icon: 'user',
        //   url: 'UserManage/UserManage'
        },
        {
          label: '设备',
          icon: 'location',
          children: [
            {
              path: '/equipmentList',
              name: 'equipmentList',
              label: '设备列表',
              icon: 'setting',
              url: 'Other/PageOne'
            },
            {
              path: '/equipmentClass',
              name: 'equipmentClass',
              label: '设备类别',
              icon: 'setting',
              url: 'Other/PageTwo'
            },
             {
              path: '/test',
              name: 'test',
              label: '测试',
              icon: 'setting',
              url: 'Other/PageTwo'
            }
          ]
        },
        {
          label: '设备2',
          icon: 'location',
          children: [
            {
              path: '/page1',
              name: 'page1',
              label: '设备列表',
              icon: 'setting',
              url: 'Other/PageOne'
            },
            {
              path: '/page2',
              name: 'page1',
              label: '设备类别',
              icon: 'setting',
              url: 'Other/PageTwo'
            },
             {
              path: '/page3',
              name: 'page3',
              label: '测试',
              icon: 'setting',
              url: 'Other/PageTwo'
            }
          ]
        }
      ]
    }
  },
  methods: {
    //跳转路由 根据名称跳转
    clickMenu(item) {
      // this.$router.push({ name: item.name })
    }
  }
}
</script>
