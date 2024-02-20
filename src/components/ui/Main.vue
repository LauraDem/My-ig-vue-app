<script>
import axios from 'axios';
export default {
  data() {
    
    return {
      posts: [],
      data: [],
      names: [
        { fullName: 'Mariello Prappapappo' },
        { fullName: 'Topo Gigio' },
        { fullName: 'Zio Paolo' },
        { fullName: 'Frank Gallager' },
        { fullName: 'Felice Manontroppo' },
        { fullName: 'Carlino Carlino' },

      ],};
  },

  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/boolgram/profiles')
      .then(profilesResponse => {
        this.data = profilesResponse.data;
        console.log(this.data);

        // Ora esegui la chiamata API dei post
        axios.get('https://flynn.boolean.careers/exercises/api/boolgram/posts')
          .then(postsResponse => {
            this.posts = postsResponse.data;
            console.log(this.posts);
          })
          .catch(error => {
            console.error('Si è verificato un errore durante la chiamata API dei post:', error);
          });
      })
      .catch(error => {
        console.error('Si è verificato un errore durante la chiamata API dei profili:', error);
      });
  },
};
</script>

<template>
  <div class="container container-fluid">
    <div class="row">
      <div class="col-8">
        <div class="top-left-side d-flex justify-content-center">
          <div class="all-stories">
            <!--!!!!!!!!! Ciclo STORIE classi round e names !!!!!!!!-->
          <div v-for="(name, index) in names" :key="index" class="round d-flex flex-column align-items-center">
            <div class="stories">
              <div class="prova-cerchio">
                <img class="pic" v-if="data[index]" :src="data[index].profile_picture" alt="Profile Image">
            </div>
        </div>
      <span class="names">
      {{ name.fullName.length > 6 ? name.fullName.slice(0, 6) + '...' : name.fullName }}
      </span>
    </div>
  </div>
</div>


<div v-for="(post, index) in posts" :key="index" class="main-left-side">
  <div class="head-main-left-side d-flex align-items-center justify-content-between">
    <div class="d-flex align-items-center">
      <div class="post-pic-profile ms-4 me-5">
        <img class="pic img-fluid" v-if="post.profile_picture" :src="post.profile_picture" alt="Profile Image">
      </div>
      <a class="text-dark" href="#">{{ post.profile_fullname }}</a>
    </div>
    <font-awesome-icon icon="fa-solid fa-ellipsis" class="dots me-4" />
  </div>
  <div class="post">
    <img class="post-image" v-if="post.post_image" :src="post.post_image" alt="Post Image">
    <p>{{ post.post_text }}</p>
  </div>
</div>
</div>

<!--colonna profili suggeriti-->
<div class="sugg col-4">
  <div class="d-flex align-items-center justify-content-between">
    <!-- profilo -->
    <div class="profile-pic ms-4">
      <img class="pic img-fluid" src="../../assets/img/grumpy-675.jpg" alt="">
    </div>
      <div class="d-flex flex-column">
        <a class="text-dark" href="#">Filippo</a>
      </div>
    <div><a class="text-info" href="#">Passa a</a></div>
</div>
<div class="sugg-profile mt-5">
  <div class="d-flex justify-content-between">
    <span class="fw-bold text-secondary">Suggerimenti per te</span>
      <a href="#" class="fw-bold text-dark">Mostra tutti</a>
  </div>
<div>
 <!-- Ciclo profili suggeriti -->
<div v-for="index in 6" :key="index" class="d-flex align-items-center mt-5 justify-content-between">
  <div class="d-flex align-items-center">
    <div class="profile-pics ms-4 me-5">
      <img class="pic" v-if="data[index]" :src="data[index].profile_picture" alt="Profile Image">
    </div>
    <a class="text-dark" href="#" v-if="posts[index] && posts[index].profile_fullname">{{ posts[index].profile_fullname }}</a>
  </div>
  <a class="text-info" href="#">segui</a>
</div>
</div>
</div>
</div>
</div>
</div>
</template>

<style lang="scss">
.top-left-side {
  max-width: 700px;
  margin-top: 50px;
  height: 200px;
  border: solid rgb(200, 200, 200);
  overflow-x: auto;

  .all-stories {
    cursor: pointer;
    display: flex;
    max-width: 100%;
    white-space: nowrap;

    .round {
      margin: 15px;
      display: inline-block; 
      justify-content: center;

      .stories {
        width: 70px; 
        height: 70px;
        border: solid black;
        border-radius: 50%;

        .prova-cerchio {
          height: 100%;
          width: 100%;
          border: solid red;
          border-radius: 50%;
          display: flex;
          justify-content: center;
          align-items: center;
          
          .pic{
            height: 60px;
            width: 60px;
            border-radius: 50%;
          }

          img{
            max-width: 100%;
          }
        }
      }

      .names {
        margin-top: 10px;
        white-space: nowrap;
      }
    }
  }
}

.main-left-side {
  max-width: 700px;
  margin-top: 50px;
  border: solid rgb(200, 200, 200);

  .head-main-left-side {
    height: 70px;
    border-bottom: solid rgb(200, 200, 200);

    .dots{
        cursor: pointer;
      }

    .post-pic-profile {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      border: solid red;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;

      .pic{
            height: 45px;
            width: 45px;
            border-radius: 50%;
          }
    }
  }
}

.post-image{
      width: 100%;
    }

.profile-pic{
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;


  .pic{
    border-radius: 50%;
  }
}

.profile-pics {
  cursor: pointer;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;

  .pic{
            height: 40px;
            width: 40px;
            border-radius: 50%;
          }

          img{
            max-width: 100%;
          }
}

.sugg {
  margin-top: 50px;
}

a{
  text-decoration: none;
}
</style>
