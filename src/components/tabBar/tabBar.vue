<template>
	<div class="tab-bar">
		<ul>
			<li v-for="(item,index) in itemList" 
				:key="index" class="tab-bar-item" 
				:class="{active: index == isActive}" 
				@click="addActive(index,item)">
				
				<span class="tab-bar-item_icon" :class="item.icon"></span>
				<span class="tab-bar-item_Text">{{item.text}}</span>
			</li>
		</ul>
	</div>
</template>
<script>
	export default{
		name:'tabbar',
		data (){
			return {
				isActive:this.$store.state.tabIndex,
				itemList:[
					// {text:"推荐",icon:"fa fa-clipboard",link:'/'},
					{icon:"fa fa-2x fa-home",link:'/things'},
					{icon:"fa fa-2x fa-bookmark-o ",link:'/all'},
					// {text:"发现",icon:"fa fa-smile-o",link:'/prearticle'},
					// {text:"发布",icon:"fa fa-pencil",link:'/designer'},
					{icon:"fa fa-2x fa-pencil",link:'/publish_all'},
					{icon:"fa fa-2x fa-user-o",link:'/personal'}
				]
			}
		},
		mounted(){
			if(this.isActive != 0){
				this.$router.push(this.itemList[this.isActive].link);
				// console.log(this.username)
			}
		},
		methods:{
			addActive: function(index,item){
				this.isActive = index;
				this.$router.push(item.link);
				this.$store.commit("changeTab",index);
			}
		}
	};
</script>