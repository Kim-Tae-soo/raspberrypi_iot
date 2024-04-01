<template>
    <v-app>
        <v-app-bar app color="primary" dark>
            <v-app-bar-nav-icon @click.stop="bDrawer=!bDrawer"></v-app-bar-nav-icon>
            <v-toolbar-title>장치 관리 페이지입니다.</v-toolbar-title>
        </v-app-bar>
        <v-navigation-drawer absolute temporary v-model="bDrawer">
            <v-toolbar flat height="100px">
                <v-list>
                    <v-list-item>
                        <v-list-item-content>
                            <v-list-item-avatar>
                                <img src="http://randomuser.me/api/portraits/men/44.jpg">
                            </v-list-item-avatar>
                            <v-list-item-title class="title">풀다운 메뉴입니다.</v-list-item-title>
                            <v-list-item-subtitle></v-list-item-subtitle>
                        </v-list-item-content>
                    </v-list-item>
                </v-list>
            </v-toolbar>
            <v-divider></v-divider>
            <v-list class="pt-3">
                <v-list-item v-for="item in items" :key="item.text" :href="item.to">
                    <v-list-item-action>
                        <v-icon>{{item.icon}}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title>{{item.text}}</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
        <v-content>
            <v-container fluid>
                <v-row>
                    <v-col>
                        <router-view></router-view>
                    </v-col>
                </v-row>
            </v-container>
        </v-content>
        <v-footer>
            <v-btn text value="서비스 안내">
                <v-icon>subway</v-icon>
            </v-btn>
        </v-footer>
    </v-app>
</template>

<script>

export default {
  name: 'App',

  data() {     
      return {
      bDrawer: false,
      items: [
        { text: '메인 콘솔', icon: 'mdi-console', to:'/'},
        { text: '사이트 소개', icon: 'mdi-star', to:'/about'},
        { text: '간단 메뉴얼', icon: 'mdi-book', to:'/manual' },
        { text: '회사 정보', icon: 'mdi-information',to:'/information' },
      ],
      }
  }
};
</script>
