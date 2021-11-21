<template>

    <div class="main">
        <p>No courses added.</p>   
    </div>
 <ul class="main">
    <li>
        <div>
            <header class="title">
                <h2>Hello</h2>
                <button>Delete</button>
            </header>
            <p class="description">
                Hello
            </p>
            <nav class="link">
                <a href="" target="_blank">View Resource</a>
            </nav>
        </div>
    </li>

    
 </ul>
  
</template>

<script>

export default {
  name: 'tabStore',
  components: {
    
  },
  data() {
    return {
        
    }
  }
}
</script>

<style scoped>
.main {
    max-width: 40%;
    height: 130px;
    background-color: #FFF;
    margin: 0 auto;
    font-family: 'Roboto', sans-serif;
}
.main li {
    padding: 0;
    margin: auto;
    max-width: 100%;
}
.main div {
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0, 0 ,0 , 0.3);
    padding: 1rem;
    margin: 2rem auto;
    max-width: 100%;
}
.main header {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.title {
    font-size: 1.2rem;
    font-weight: bold;
    color: #000;
    font-family: inherit;
}
.title button {
    font-size: 1rem;
    padding: 0.75rem;
    font-family: inherit;
    color: #3a0061;
    margin: 0 15px;
    border: none;
    outline: none;
    cursor: pointer;
    border: 1px solid transparent;
    transition: all 0.5s;
    border-radius: 10px;
    background-color: #FFF;
}
.title button:hover {
    background-color: rgba(39, 0, 65, 0.5);
    border-color: #FFF;
}

.title button:active {
    background-color: rgba(39, 0, 65, 1);
    border-color: #FFF;
    color: #FFF;
}
.description {
    margin: 0.5rem 0;   
    font-family: inherit;
    font-size: 1rem;
    font-style: normal;
}
.link {
    margin: 0.5rem 0;   
}
.link a{
    text-decoration: none;
    color: #ce5c00;
}
</style>
