<template>
    <div class="contactpage" id="contact">
        <div class="contactcontainer">
            <h2 data-aos="fade-down">Contact me</h2>
            <div class="contact">
            <form data-aos="zoom-out-right" action="mailto:joepvermeij@gmail.com?subject=PortfolioMessage" method="post" enctype="text/plain">
            <div class="formitem">
                <label for="name">Name
                <input class="textinput"
                type="text" name="name" id="name" />
                </label>
            </div>
            <div class="formitem">
                <label for="email">Email
                <input class="textinput" type="text" name="email" id="email" />
                </label>
            </div>
            <div class="formitem">
                <label>Message</label>
                <br />
                <textarea name="Message"></textarea>
            </div>
            <div>
                <input type="submit" name="submit" value="SEND" />
            </div>
            </form>
            <div data-aos="zoom-out-left"  class="extrainfo">
                <div class="telephone">
                <h3>Telephone</h3>
                <p><a href="tel:0032487710069">+32 4 87 71 00 69</a></p>
                </div>
                <div class="email">
                <h3>E-mail</h3>
                <p><a href="mailto:joepvermeij@gmail.com">joepvermeij@gmail.com</a></p>        
                </div>
                <div class="linkedin">
                <h3>Linkedin</h3>
                <p><a href="https://www.linkedin.com/in/joepvermeij/">www.linkedin.com/in/joepvermeij/</a></p>        
                </div>
                <div class="linkedin">
                <h3>Curriculum Vitae</h3>
                <p><a :href="`${publicPath}Joep_Vermeij_CV_English.pdf`" download="">English</a></p>
                <p><a :href="`${publicPath}Joep_Vermeij_CV.pdf`" download="">Nederlands</a></p>        
                </div>
            </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ContactPage',
    data() {
        return {
            publicPath: process.env.BASE_URL
        }
    },
    methods: {
        GoToContact(){
            var element = document.getElementById('contact');
            var top = element.offsetTop;
            window.scrollTo(0, top-100);
        },
    },
}
</script>

<style scoped>
.contactpage{
    height: calc(100vh - 6rem);
    width: 100%;
    background: var(--accent-black);
    color: var(--accent-white);
}
.contactcontainer{
    margin-left: 50%;
    width: 50%;
}
h2{
    font-size: 4rem;
    margin: 0;
    padding: 3rem 0 1rem 0;
}
.formitem{
    margin-top: 1rem;
}
label{
    font-size: 2rem;
}
input{
    background: var(--accent-white);
    display: block;
    font-size: 2rem;
}
input[type=submit]{ 
  font-family: Staatliches, Roboto, sans-serif;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 2rem;
  margin: 1rem;
  width: 15rem;
  cursor: pointer;
}
textarea{
    background: var(--accent-white);
    font-size: 1.5rem;
    width: 30rem;
    height: 10rem;
    padding: 1rem;
    border: none;
    border-radius: 0.5rem;
    width: 90%;
}
textarea:focus, .textinput:focus{
    outline: none;
}
h3{
    font-size: 2rem;
    margin: 1rem 0 0 0;
}
.textinput{
    width: 30rem;
    padding: 1rem;
    border: none;
    border-radius: 0.5rem;
    width: 90%;
}
.extrainfo {
    display: flex;
    flex-direction: column;
    padding: 2rem;
    margin: 0 1%;
    border: 0.2rem solid var(--accent-white);
    border-radius: 1rem;
    width: 35%;
}
form{
    padding: 2rem;
    border: 0.2rem solid var(--accent-white);
    border-radius: 1rem;
    width: 60%;
}
.contact{
    display: flex;
}
p{
    font-size: 1.3rem;
}
a{
    text-decoration: none;
    color: var(--accent-white);
}
@media (hover: hover) {  
    input[type=submit]:hover{
        background: var(--accent-purple);
    }
    a:hover{
        color: var(--accent-purple);

    }
}
@media only screen and (max-width: 1200px) {
    input[type=submit]:active{
        background: var(--accent-purple);
    }
    a:active{
        color: var(--accent-purple);

    }
    .contactcontainer{
        width: 100%;
        margin: 0;
    }
    .contact{
        display: flex;
        flex-direction: column;
        width: 100%;
    }
    form{
        margin: 2%;
        width: calc(100% - 4.4rem - 4%);
    }
    .textinput, textarea{
        width: 90%;
    }
    h2{
        margin: 0 1rem;
    }
    .extrainfo{
        margin: 2%; 
        width: calc(100% - 4.4rem - 4%);
    }
}
</style>