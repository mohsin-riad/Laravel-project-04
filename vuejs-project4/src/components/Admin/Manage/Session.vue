<template>
    <div>
        <br>
        <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
                <li class="breadcrumb-item"><a href="#">Dashboard</a></li>
                <li class="breadcrumb-item active" aria-current="page">Manage</li>
                <li class="breadcrumb-item active" aria-current="page">Session</li>
            </ol>
        </nav>
        <hr>
        <div class="row">
            <div class="col-sm-9 col-md-7 col-lg-6 mx-auto">
                <div class="card text-white bg-dark">
                    <div class="card-header">Manage</div>
                    <div class="card-body">
                        <h5 class="card-title text-center">Manage Session</h5>
                        <form @submit.prevent="activeSession" class="form-signin">

                          <div class="">
                              <label for="inputSession">Choose Session</label>
                              <select id="inputSession" v-model="session" class="form-control text-white bg-dark" required>
                                  <option v-for="s in sessions" v-if="!s.status" :key="s.id" :value="s.id" >{{s.name}}</option>
                              </select>
                              <label for=""></label>
                          </div>

                          <button class="btn btn-lg btn-success btn-block text-uppercase" type="submit">Active</button>

                          <!-- <div v-if="msg" class="form-label-group">
                              <hr>
                              <div class="alert alert-success alert-dismissible">
                                  <button type="button" class="close" data-dismiss="alert">&times;</button>
                                  <strong>{{ msg }}</strong>
                              </div>
                          </div> -->
                      </form>
                      <br>
                      <form @submit.prevent="deactiveSession" class="form-signin">

                          <div class="">
                              <label for="inputSemester">Choose Session</label>
                              <select id="inputSemester" v-model="session" class="form-control text-white bg-dark" required>
                                  <option v-for="s in sessions" v-if="s.status" :key="s.id" :value="s.id">{{s.name}}</option>
                              </select>
                              <label for=""></label>
                          </div>

                          <button class="btn btn-lg btn-danger btn-block text-uppercase" type="submit">Deactive</button>

                          <!-- <div v-if="msg" class="form-label-group">
                              <hr>
                              <div class="alert alert-success alert-dismissible">
                                  <button type="button" class="close" data-dismiss="alert">&times;</button>
                                  <strong>{{ msg }}</strong>
                              </div>
                          </div> -->
                      </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            sessions: [],
            session: null,
            msg: null
        }
    },
    mounted(){
        this.getSession();
        
    },
    methods: {
        getSession(){
            const baseURI = 'http://127.0.0.1:8000/api/get-session'
            this.$http.get(baseURI)
            .then((res)=>{
                this.sessions = res.data.sessions
                this.msg = res.data.msg
            })
            
            //console.log(this.sessions);
        },
        async activeSession() {
            const baseURI = 'http://127.0.0.1:8000/api/update-session'
            this.$http.post(baseURI, {
                id : this.session,
                status: 0
            })
            .then((res)=>{
                this.msg = res.data.msg;
                this.session = null;
                //this.sessions = [];
                alert(this.msg)
            })
            
            
         },
        async deactiveSession() {
            const baseURI = 'http://127.0.0.1:8000/api/update-session'
            this.$http.post(baseURI, {
                id : this.session,
                status: 1
            })
            .then((res)=>{
                this.msg = res.data.msg;
                this.session = null;
                //this.sessions = [];
                alert(this.msg)
            })
            
         }
    },
        
}
</script>
<style>
:root {
  --input-padding-x: 1.5rem;
  --input-padding-y: .75rem;
}

.breadcrumb {
    margin-bottom: 0;
    background-color:  #00000036;
    font-weight: bold;
}

.card-signin {
  border: 0;
  border-radius: 1rem;
  box-shadow: 0 0.5rem 1rem 0 rgba(0, 0, 0, 0.1);
}

.card-signin .card-title {
  margin-bottom: 2rem;
  font-weight: 300;
  font-size: 1.5rem;
}

.card-signin .card-body {
  padding: 2rem;
}

.form-signin {
  width: 100%;
}

.form-signin .btn {
  font-size: 80%;
  border-radius: 0.5rem;
  letter-spacing: .1rem;
  font-weight: bold;
  padding: 1rem;
  transition: all 0.2s;
}

.form-label-group {
  position: relative;
  margin-bottom: 1rem;
}

.form-label-group input,
.form-label-group select {
  height: auto;
  border-radius: 2rem;
}

.form-label-group>input,
.form-label-group>label {
  padding: var(--input-padding-y) var(--input-padding-x);
}

.form-label-group>label {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  margin-bottom: 0;
  /* Override default `<label>` margin */
  line-height: 1.5;
  color: #495057;
  border: 1px solid transparent;
  border-radius: .25rem;
  transition: all .1s ease-in-out;
}

.form-label-group input::-webkit-input-placeholder {
  color: transparent;
}

.form-label-group input:-ms-input-placeholder {
  color: transparent;
}

.form-label-group input::-ms-input-placeholder {
  color: transparent;
}

.form-label-group input::-moz-placeholder {
  color: transparent;
}

.form-label-group input::placeholder {
  color: transparent;
}

.form-label-group input:not(:placeholder-shown) {
  padding-top: calc(var(--input-padding-y) + var(--input-padding-y) * (2 / 3));
  padding-bottom: calc(var(--input-padding-y) / 3);
}

.form-label-group input:not(:placeholder-shown)~label {
  padding-top: calc(var(--input-padding-y) / 3);
  padding-bottom: calc(var(--input-padding-y) / 3);
  font-size: 12px;
  color: #777;
}
</style>