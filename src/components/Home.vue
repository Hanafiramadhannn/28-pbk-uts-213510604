<template>
    <div class="home-container">
      <h1>Welcome to My Website</h1>
      <p>This is the homepage of my website.</p>
      <div class="cta-buttons">
        <router-link to="/task" class="btn btn-primary">View Task List</router-link>
        <router-link to="/about" class="btn btn-secondary">Learn More About Me</router-link>
      </div>
    </div>
  </template>
  
  <style>
  .home-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #F5F5F5;
  }
  
  h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
  }
  
  p {
    font-size: 1.5rem;
    margin-bottom: 2rem;
  }
  
  .cta-buttons {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .btn {
    display: inline-block;
    padding: 1rem 2rem;
    margin: 0.5rem;
    font-size: 1.2rem;
    font-weight: bold;
    text-transform: uppercase;
    text-decoration: none;
    color: white;
    background-color: #06283D;
    border-radius: 0.25rem;
    transition: all 0.2s ease-in-out;
  }
  
  .btn:hover {
    background-color: #FDB813;
    color: #06283D;
  }
  
  .btn-primary {
    background-color: #06283D;
  }
  
  .btn-secondary {
    background-color: #FDB813;
    color: #06283D;
  }
  </style>  