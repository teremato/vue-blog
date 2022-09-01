<template>
  <article class="post">
    <div class="post_user_info">
        <div class="user_avatar">{{ getShortName }}</div>
        <div>
            <div class="user_company">Company</div>
            <div>{{ user.company.name }}</div>
        </div>
    </div>
    <div class="title">{{ post.title }}</div>
    <div class="body">{{ post.body }}</div>
  </article>
</template>

<script>
export default {
    name: 'post-item',
    data() {
        return {
            user: {
                name: 'anton bugakov',
                company: {
                    name: ''
                }
            }
        }
    },
    props: {
        post: {
            type: Object
        }
    },
    mounted() {
        this.getCurrentUser(this.post.userId)
        .then(data => this.user = {
            ...this.user,
            name: data.name,
            company: {
                name: data.company.name
            }
        })
    },
    methods: {
        async getCurrentUser(userID) {
            return fetch(`https://jsonplaceholder.typicode.com/users/${userID}`)
            .then(response => response.json())
            .then(data => data)
        }
    },
    computed: {
        getShortName() {
            let short =  this.user.name.split(' ');
            short = short.map((text) => {
                return text.toUpperCase().slice(0, 1)
            })
            return short.join('')
        }
    }
}
</script>

<style scoped>
    .post {
        padding: 10px;
        margin: 10px;
        border-radius: 10px;
        
        background-color: white;
        box-shadow: 0px 0px 24px -2px rgba(34, 60, 80, 0.2);
    }
    .post_user_info {
        margin: 10px 0px;

        display: flex;
        align-items: center;
        gap: 10px;
    }
    .user_avatar {
        padding: 10px;
        border-radius: 50%;
        background-color: crimson;
        color: white;
    }
    .user_company {
        color: grey;
    }
    .title {
        font-size: 20px;
        margin-bottom: 10px;
    }
    .body {
        width: 50%;
        color: gray;
    }
</style>