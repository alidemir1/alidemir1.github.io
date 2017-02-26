---
layout: post
title:  "Q-Learning Algorithm and Basic Application on Arduino"
date:   2017-02-26
excerpt: "Q-Learning algorithm is unsupervised learning algorithm in order to make a system learning by itself."
tag:
- Q - Learning
- Machine Learning
- Unsupervised Learning
- Reinforcement Learning
comments: false
---
### Machine Learning
Actually before starting to explain Q-Learning Algorithm. I would like to write things down about Machine Learning (ML) which we started to
hear more frequently from day to day. Applications of ML varying from Autonomous cars [1], [3] to visualizing/immitating what people see under 
effect of the hallucinatives [2] so, from **engineers** to **physcologists**. But why are we hearing most commonly right now and not before. It is
actually a not a new area of research, you can actually see an autonomous car based on ML [3] from 1989. In my perspective it is because 
it was too expensive computationally. It still is but not like in the 1980s. Of course not only this, 
also there was not enough data to train (teach) models in order to make them do what we want them to do. So ImageNet[4] was born and 
now we have data and higher computational powers in our hands than 1980s. So we can teach a car to drive itself, or make a robot to "watch
and learn" like we do in our daily life. But don't worry they are not even close there to start a war against us :).

### Q-Learning
If you open the <a href="https://github.com/alidemir1/MachineLearningOnArduinoUno/blob/master/Machine_Q_Learning/Machine_Q_Learning.ino" rel="nofollow">code</a> 
while reading it might ease your understanding and if you make any improvements please let me know.
Q-Learning is one of the basic unsupervised learning algorithm. I am going to explain this algorithm by an example. Now, imagine that you
have robot and a house with six rooms. Task of the robot is the bring you whatever you want from kitchen to your study room. You want robot
to learn the shortest way between these two rooms. I am hearing some objections why I am not programming it in conventional ways. Of course
you can, but I am trying to explain somthing :). Whatever, let's get to the point. Now you are creating a reward matrix of all the roads with rewards. You are
assigning -1 to the walls (can't pass), 0 for possible passing ways, and lastly reward (some big number (e.g. 100)) for your study room.
By the way imagine this matrix that reward[x,y]; where x is the robot's current room number, and map[x,y] is the assigned number for passage way from x to y, 
so if there is passage from x to y then it is 0 (while y is not the study room otherwise it is 100), if there is no then it is -1. Now,
our reward matrix is ready, and we need to initialize some learning matrix. We are initializing learning (Q) matrix as matrix of zeros with same 
dimension with reward matrix. Lastly, we need to formulize learning; 

{% highlight ruby %}
while(i < iterate){ //repeats learning for true result 
  while(current room != study room){ //Try different actions and learns untill go to the study room
        action = random_possible_actions
        Q[current room, action] = reward[current room, action] + alpha*max[Q[action, all actions]]
        current room = action
}
i++;
}
{% endhighlight %}

Where alpha is learning rate (0.8). By the way, don't calculate actions rewarded with "-1" since robots can not get through walls :). You should iterate this line of code 
as much as you believe is enough for robot to learn. While iterating you should assign your  actions randomly, so your robot be able to try different roads.

You got your robot learn the road, but how you can test it. Testing code as follows

{% highlight ruby %}
current room = choose some room other than study room
while(current room != study room){
     current room= index(max[Q[current room, all actions]]) //choosing the next room with highest learned reward
     print current room   
 }
{% endhighlight %}

If you room numbers are sequence that creates the shortest way. Then you accomplished to teach your robot the shortest way from kitchen
to your study room. 
Video is also available if you want check; 

<iframe width="560" height="315" src="//www.youtube.com/embed/uvj-GhsljyA" frameborder="0"> </iframe>


### References
###### [1]  S. Shalev-Shwartz, S. Shammah,Amnon Shashua, "Safe, Multi-Agent, Reinforcement Learning for Autonomous Driving", October 2016.

###### [2] Google's Deep Dream Algorithm at "https://github.com/google/deepdream", accessed on 26th February 2017/

###### [3] Dean Pomerleau , "ALVINN: An Autonomous Land Vehicle In a Neural Network," Advances in Neural Information Processing Systems 1, 1989.

###### [4] Jia Deng, Wei Dong, R. Socher, Li-Jia Li, Kai Li and Li Fei-Fei, "ImageNet: A large-scale hierarchical image database", 2009 IEEE Conference on Computer Vision and Pattern Recognition, 2009.
