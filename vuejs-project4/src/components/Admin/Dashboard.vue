<template>
    <div class="container">
        <br>
        <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
                <li class="breadcrumb-item"><a href="#">Dashboard</a></li>
            </ol>
        </nav>
        <hr>
        <div class="row">
            <div class="col-sm-9 col-md-7 col-lg-6 mx-auto">
                <div class="card dark text-white bg-dark">
                    <div class="card-body">
                        <h5 class="card-title text-center">Welcome To Admin Dashboard</h5>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>
<style>
:root {
  --input-padding-x: 1.5rem;
  --input-padding-y: .75rem;
}

body {
  background: #525252;
  background: linear-gradient(to right, #414141ee, #1d1d1d);
}
.breadcrumb {
    margin-bottom: 0;
    background-color:  #00000036;
    font-weight: bold;
}
.dark {
  border: 0;
  border-radius: 1rem;
  box-shadow: 0 0.5rem 1rem 0 rgba(0, 0, 0, 0.1);
}

.dark .card-title {
  margin-bottom: 2rem;
  font-weight: 300;
  font-size: 1.5rem;
}

.dark .card-body {
  padding: 2rem;
}
</style>