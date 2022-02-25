<template lang="">
    <div>
        
    </div>
</template>
<script>
import { ref } from 'vue'
import { collectionPosts } from '../firebase/confi'
export default {
    
    setup() {
        
        const posts = ref([]);
        const load = async() => {
            const res = await collectionPosts.collection('posts').get();
            posts.value = res.docs.map(doc => {
                return { ...doc.data(), id: doc.id }
            })
        }

        load();
        return { posts, load }
    }
}
</script>
<style lang="">
    
</style>