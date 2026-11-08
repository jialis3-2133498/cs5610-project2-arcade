<svelte:head>
    <title>About | Jiali Sheng's Arcade</title>
    <meta
        name="description"
        content="Learn about my background, education, and experience."
    />
</svelte:head>

<script>
    import { asset } from '$app/paths';
</script>

<h1>Who is Jiali Sheng?</h1>
<section>
    <h2>About Me</h2>
    <img
        class="profile-photo"
        src={asset('images/Jiali_Sheng_Photo.png')}
        alt="Portrait of Jiali Sheng"
    />    
    <p>
        I am from China and now live in Seattle. Seattle is my favorite city on the planet so far!
        I like to run, cook, go to the gym, hike, listen to music, and watch movies!
    </p>
</section>
<section>
    <h2>Education</h2>
    <p>
        I earned my Bachelor of Arts degree in Economics from the University of Washington. 
        Studying economics has given me a different perspective on how the world works through 
        the lens of money and resources. After graduating from UW in June 2025, I began a new 
        chapter at Northeastern University in Seattle. I am currently pursuing a Master of Science 
        in Computer Science and am interested in exploring interdisciplinary career opportunities at 
        the intersection of economics and computer science.
    </p>

</section>

<section>
    <h2>Experience</h2>
    <p>
        During my undergraduate studies at UW, I had two part-time on-campus jobs. My first role was 
        as a Student Coordinator in a campus dining hall, where I enjoyed working with people from 
        diverse academic and cultural backgrounds. My second job was as a Student Specialist at UW Libraries. 
        Through that experience, I learned the importance of reliable software systems and how they can support 
        accuracy and efficiency when managing a large volume of daily updates. 
    </p>
</section>


