---
title: "Custom Mouse Cursor Tutorial"
date: "2020-11-03 05:09:30 +0200"
author: NrdyBhu1
category: tutorial blog 
---

So today we are going to be making custom mouse cursor in unity. 

{: .note .info}
Currently I am using `Unity 2019.4.10`, So this can be applicable for future versions and maybe some older ones too. 


We shall start with the default `Sample Scene` \
\
I use [VS-Code IDE](https://code.visualstudio.com) as it is light weight, but you can use any IDE of your choice. \
Download the assets here to get started along with me. \
\
\
<a href="{{ '/zips/Assets.zip' | relative_url }}"><button>Download Assets <i class="fas fa-download"></i></button></a> \
\
\
Lets start by creating a C# script and call it GameManager.cs \
so this is the default script you will get 


{% highlight cs %}
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
First we are going to declare 2 texture2ds before our start function and call them hand and pointer. 


{% highlight cs %}

    public Texture2D pointer;
    public Texture2D hand;

{% endhighlight %}
\
\
You can delete the Update function but leave the Start function as it is. \
Now we will create 2 functions and call it setPointer and setHand. 



{% highlight cs %}

    public void setHand(){
        
    }

    public void setPointer(){
        
    }

{% endhighlight %}
\
\
You can use Cursor.SetCursor() function to set the cursor through script. \
It requires 3 parameters texture vector2 hotspot and cursormode. \
We`ll set the hotspot to 0,0 and cursormode to force-software. 



{% highlight cs %}
    public void setHand(){
        Cursor.SetCursor(hand, new Vector2(0, 0), CursorMode.ForceSoftware);
    }

    public void setPointer(){
        Cursor.SetCursor(pointer, new Vector2(0, 0), CursorMode.ForceSoftware);
    }
{% endhighlight %}
\
\
And so this is the final script. 



{% highlight cs %}
    using UnityEngine;

    public class GameManager : MonoBehaviour
    {
        public Texture2D pointer;
        public Texture2D hand;

        void Start()
        {
            setPointer();
            //setting the cursor to pointer on start
        }

        public void setHand(){
            Cursor.SetCursor(hand, new Vector2(0, 0), CursorMode.ForceSoftware);
        }

        public void setPointer(){
            Cursor.SetCursor(pointer, new Vector2(0, 0), CursorMode.ForceSoftware);
        }
    }
{% endhighlight %}
\
\
Now go into the unity editor and hit play. \
Everything should work as expected. \
\
\
<a href="https://github.com/NrdyBhu1/Custom-Mouse-Cursor/archive/master.zip"><button>Download project files <i class="fas fa-download"></i></button></a> 