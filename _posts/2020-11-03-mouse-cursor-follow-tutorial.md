---
title: "Mouse Cursor Follow Tutorial"
date: "2020-11-03 07:26:47 +0200"
author: NrdyBhu1
category: tutorial blog 
---

 So today we are going to be making and object follow the mouse cursor in unity. 

{: .note .info}
Currently I am using `Unity 2019.4.10`, So this can be applicable for future versions and maybe some older ones too. 


We shall start with the default `Sample Scene` \
\
\
<a href="{{ '/zips/Follow.zip' | relative_url }}"><button>Download Assets <i class="fas fa-download"></i></button></a> \
\
\
Lets start by creating a C# script and call it MouseCursorFollow.cs \
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
Now we are going to declare all our variables. 


{% highlight cs %}
    public Camera myCam;
    Vector2 mousePosition;
    RigidBody2D rb;
{% endhighlight %}
\
\
Now reference the scene camera to the game object which has this script attached. \
Next attach a RigidBody2D component to this game object and set the gravityScale to 0 \
Get the RigidBody2D component through the start function. 


{% highlight cs %}
    void Start(){
        rb = GetComponent<RigidBody2D>();
    }
{% endhighlight %}
\
Now we will set our local mousePosition variable to the actual mousePosition \
and convert it with Screen to World point function from our cam. 


{% highlight cs %}
    void Update(){
        mousePosition = myCam.ScreenToWorldPoint(Input.mousePosition);
    }
{% endhighlight %}
\
\
And we move our current position to the mousePosition with MovePosition from RigidBody2D. 

{% highlight cs %}
    void Update(){
        mousePosition = myCam.ScreenToWorldPoint(Input.mousePosition);
        rb.MovePosition(mousePosition);
    }
{% endhighlight %}

So this is the final script. 

{% highlight cs %}
    using UnityEngine;

    public class GameManager : MonoBehaviour
    {
        public Camera myCam;
        Vector2 mousePosition;
        RigidBody2D rb;

        void Start(){
            rb = GetComponent<RigidBody2D>();
        }

        void Update(){
            mousePosition = myCam.ScreenToWorldPoint(Input.mousePosition);
            rb.MovePosition(mousePosition);
        }
    }
{% endhighlight %}
\
\
Now go into the unity editor and hit play. \
Everything should work as expected. \
\
\
<a href="https://github.com/NrdyBhu1/Mouse-Cursor-Follow/archive/master.zip"><button>Download project files <i class="fas fa-download"></i></button></a> 