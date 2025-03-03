<script lang="ts">
    import logo from "$lib/images/gozar-productions-logo.svg";
</script>

<header>
    <hgroup>
        <div>
            <h1>Gozar Productions</h1>
            <h2>Code</h2>
        </div>
        <img src={logo} alt="Gozar Productions Logo" />
    </hgroup>
    <hr class="vertical-rule" />
    <nav>
        <ul>
            <li>
                <a href="/">Home</a>
            </li>
            <li>
                <a href="/projects">Our Projects</a>
                <ul>
                    <li>
                        <a href="/obsidian">Obsidian</a>
                        <ul>
                            <li><a href="/obsidian/diarian">Diarian</a></li>
                            <li>
                                <a href="/obsidian/colored-candy"
                                    >Colored Candy</a
                                >
                            </li>
                        </ul>
                    </li>
                    <li>
                        <a href="/discord">Discord Bots</a>
                        <ul>
                            <li>
                                <a href="/discord/voicely-text">Voicely Text</a>
                            </li>
                            <li>
                                <a href="/discord/voicely-ping">Voicely Ping</a>
                            </li>
                        </ul>
                    </li>
                </ul>
            </li>
            <li>
                <a href="#contact">Contact</a>
            </li>
            <li>
                <a href="https://www.gozarproductions.com">Back</a>
            </li>
        </ul>
    </nav>
</header>

<style>
    hgroup {
        display: flex;
        align-items: center;
        justify-content: center;
        width: max-content;
        padding: 10px;
        margin: 0px;
        transition: background-color 0.3s;
        & > img {
            aspect-ratio: 1 / 1;
            height: 4em;
            vertical-align: middle;
        }
        & h1,
        & h2 {
            text-align: right;
            padding: 0px;
            margin: 0px;
        }
        & > :first-child {
            margin: 0px;
            margin-right: 0.4em;
        }
        & > :last-child {
            margin: 0px;
            margin-left: 0.4em;
        }
    }

    header {
        display: flex;
        justify-content: center;
        width: 100%;
        background-color: hsl(245, 37%, 17%);
        position: fixed;
        top: 0;
        left: 0;
    }

    nav {
        display: flex;
        align-items: center; /* Center items vertically */
        & a {
            color: inherit;
            font-weight: initial;
            display: flex;
            align-items: center;
            padding: 6px 10px;
            &:hover {
                text-decoration: none;
            }
        }
        & ul {
            list-style-type: none;
            padding: 0px;
        }
        & > ul {
            height: 100%;
            display: flex;
            & li {
                text-align: center;
                position: relative;
                width: max-content;
                &:hover {
                    & > a {
                        background-color: rgba(0, 0, 0, 0.2);
                        /* color: black; */
                    }
                    & > ul {
                        display: block; /* Show nested ul on hover */
                    }
                }
            }
            & > li {
                height: 100%;
                box-sizing: border-box;
                & > a {
                    height: 100%;
                    box-sizing: border-box;
                }
                & ul {
                    display: none; /* Hide nested ul by default */
                    position: absolute; /* Position it absolutely */
                    background-color: hsl(245, 37%, 17%);
                    & li {
                        width: max-content;
                        min-width: 100%;
                        margin: auto;
                        box-sizing: border-box;
                    }
                }
                & > ul {
                    left: 0; /* Align to the left of the parent li */
                    top: 100%; /* Position it below the parent li */
                    & ul {
                        right: 100%;
                        top: 0;
                    }
                }
            }
        }
    }

    hr.vertical-rule {
        border: none;
        border-left: 1px solid rgba(255, 255, 255, 0.7); /* Change color and width as needed */
        height: 48px; /* Set the height of the line */
        margin: auto 20px; /* Optional: add some margin */
    }
</style>
