---
title: "Pause Menu Tutorial"
date: "2020-11-03 07:45:12 +0200"
author: NrdyBhu1
category: tutorial blog 
---

So today we are going to be making pause menus in unity. 

{: .note .info}
Currently I am using `Unity 2019.4.10`, So this can be applicable for future versions and maybe some older ones too. 


I have a pre-prepared scene with only particles moving randomly. \
\
\
<a href="{{ '/zips/BlurShader.zip' | relative_url }}"><button>Download Assets <i class="fas fa-download"></i></button></a> \
\
\
Lets start by creating a C# script and call it GameManager.cs \
so this is the default script you will get 


{% highlight cs %}
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class GameManager : MonoBehaviour{
        
        //Use..
        void Start(){
            
        }

        //....
        void Update(){

        }
    }
{% endhighlight %}
\
\
You can remove both the comments. \
First create a canvas with all the elements to be displayed when the game is paused and disable it.\
Rename the canvas to PauseCanvas or what you choose. 

We will use Time.timeScale to change the active state of the game. \
When its value is 0 then the game will like stop and if it is 1 it will run properly. 
It is like the speed of the game, it won`t work or move if it 0. \
We will create 2 functions Resume and Pause and change the timeScale value here.

{% highlight cs %}
    void Pause(){
        Time.timeScale = 0;
    }

    void Resume(){
        Time.timeScale = 1;
    }

{% endhighlight %}

And we will modify the visibility of the pause menu too.
So the with the additional code it will be 

{% highlight cs %}
    void Pause(){
        if(pauseCanvas != null){
            pauseCanvas.gameObject.SetActive(true);
            Time.timeScale = 0;
        }
    }

    public void Resume(){
        if(pauseCanvas != null){
            pauseCanvas.gameObject.SetActive(false);
            Time.timeScale = 1;
        }
    }
{% endhighlight %}

And we will disable the pause menu on start. 

{% highlight cs %}
    private void Start() {
        if(pauseCanvas != null){
            pauseCanvas.gameObject.SetActive(false);
        }
    }
{% endhighlight %}

So this is the Final Script.

{% highlight cs %}
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class GameManager : MonoBehaviour
    {
        #region Variables
        public Canvas pauseCanvas = null;
        #endregion
        private void Start() {
            if(pauseCanvas != null){
                pauseCanvas.gameObject.SetActive(false);
            }
        }

        void Pause(){
            if(pauseCanvas != null){
                pauseCanvas.gameObject.SetActive(true);
                Time.timeScale = 0;
            }
        }

        public void Resume(){
            if(pauseCanvas != null){
                pauseCanvas.gameObject.SetActive(false);
                Time.timeScale = 1;
            }
        }

        private void Update() {
            if(Input.GetKey("escape")){
                Pause();
            }
        }
    }
{% endhighlight %}


\
\
Now go into the unity editor and hit play. \
Everything should work as expected. \
Hit the Escape key to pause the game. \
\
\
<a href="https://github.com/NrdyBhu1/Custom-Mouse-Cursor/archive/master.zip"><button>Download project files <i class="fas fa-download"></i></button></a> 