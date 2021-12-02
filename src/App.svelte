<script lang="ts">
  import Fa from 'svelte-fa'
  import { faClock } from '@fortawesome/free-solid-svg-icons'
  let currPos = window.scrollY + 400;

  document.addEventListener("scroll", () => {
    currPos = window.scrollY + 400;
  });

  import timelineData from "./assets/timeline.json";
  const data: {
    title: string;
    date: string;
    description: string;
    image?: string;
  }[] = timelineData;
</script>

<main>
    <div class="svg-timeline">
    </div>
    <div class="timeline">
        {#each data as timeElement}
          <div class="timeline-card">
            <h3>{timeElement.title}</h3>
            <span class="muted">{timeElement.date}</span>
            {#if timeElement.image }
              <img alt={timeElement.title} src={timeElement.image}/>
            {/if}
            <p>{timeElement.description}</p>
          </div>
        {/each}
    </div>
</main>

<style>

  .timeline-card img {
    margin-top: 1rem;
    border-radius: 15%;
    width: 150px;  
  }
    
  .timeline-card {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    margin-bottom: 4rem;
    min-height: 3rem;
    background-color: #313131;
    color: white;
    padding: 1.5rem;
    width: 75%;
  }

  .svg-timeline {
    position: absolute;
    left: 50%;
    top: 0;
    margin-top: 1rem;
  }

  main {
    padding: 1.5rem;
    /*height: 100vh;*/
  }

  .timeline-circle {
    display: grid;
    right: 1.5rem;
    top: 3rem;
    position: absolute;
  }

  .muted {
    color: #c3c3c3;
  }
</style>
