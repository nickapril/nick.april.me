---
layout: post
title:  "Rails Web Application"
date:   2017-05-30 00:00:00
img: TA-main.png
description: This Ruby on Rails Web application was built last spring to help improve student learning in large university classes. TA OnDemand standardizes teaching assistant office hour scheduling and provides a space for virtually hosted office hours. This application will encourage interaction among teaching assistants and students and therefore improve the quality of student learning.
---


### Introduction
Going in to this project, the only programming experience I had was in Java. This rails app was allowed me to experiement with many new languages and skills like Ruby, Rails, JavaScript, HTML, CSS, Web Development, Agile Development, SQL databases, AWS S3 and GIT.

Check out the github Repo here: [TA OnDemand](https://github.com/adiberk/TA)

TA OnDemand consists of three main features:
1. Dynamic scheduler 
2. Appointments
3. Live chat

Although my two teammates and I contributed to all parts of this app, most of my work was on developing live chat.

### Live Chat
The Live Chat feature uses Action Cable to seamlessly integrate WebSockets with the rest of a Rails application. If you aren't familiar with Websocets, it basically allows an open communication session to begin between a browser and a server. This allows the user to send messages to a server and receive responses without having to poll the server for a reply. Action Cable also provides a JavaScript framework for developers which also allowed for easy access to the models of this rails app written with Active Record. 

A simple channel for client-server communication

{% highlight ruby %}
class ConversationChannel < ApplicationCable::Channel
  def subscribed
    stream_from "conversations-#{current_user.id}"
  end

  def unsubscribed
    stop_all_streams
  end

  def speak(data)
    message_params = data['message'].each_with_object({}) do |el, hash|
      hash[el.values.first] = el.values.last
    end

    Message.create(message_params)
  end
end
{% endhighlight %}


Broadcasting and receiving messages with Action Cable
{% highlight ruby %}
  def broadcast_to_sender(user, message)
    ActionCable.server.broadcast(
      "conversations-#{user.id}",
      message: render_message(message, user),
      conversation_id: message.conversation_id
    )
  end

  def broadcast_to_recipient(user, message)
    ActionCable.server.broadcast(
      "conversations-#{user.id}",
      window: render_window(message.conversation, user),
      message: render_message(message, user),
      conversation_id: message.conversation_id
    )
  end

  def render_message(message, user)
    ApplicationController.render(
      partial: 'messages/message',
      locals: { message: message, user: user }
    )
  end
{% endhighlight %}

As you can see here, Action Cable subscribes users to specific "chat rooms" and will render and receive messages associated with that channel. This structure can withstand multiple channels from a single user, allowing someone to hold many private conversations at once.


![alt text](/assets/img/TA-chat.png?raw=true "Rails chat feature")

A list of all the TA's for this user's classes is in the sidebar on the left. The green circle next to Hao and Adi indicates that they are currently hosting office hours. A user can click on any of those names and a chat box will appear.





