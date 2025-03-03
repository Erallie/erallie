<script lang="ts">
    let { title, children } = $props();
</script>

<section id={title.toLowerCase().replaceAll(" ", "-").replaceAll("'", "")}>
    <h1>{title}</h1>
    <hr />
    {@render children()}
</section>

<style>
    section {
        background-color: rgba(0, 0, 0, 0.2);
        border-radius: 40px;
        margin: 40px auto;
        width: 500px;
        padding: 40px;
    }
    hr {
        width: 100px;
        margin: 1em 0px;
        margin-left: 2px;
        padding: 0px;
    }
</style>
