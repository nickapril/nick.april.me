---
layout: post
title:  "Rails Web Application"
date:   2017-05-30 00:00:00
img: TA-main.png
description: This Ruby on Rails Web application was built last spring to help improve student learning in large university classes. TA OnDemand standardizes teaching assistant office hour scheduling and provides a space for virtually hosted office hours. This application will encourage interaction among teaching assistants and students and therefore improve the quality of student learning.
---

TA OnDemand consists of three main features:
1. Dynamic scheduler 
2. Appointments
3. Live chat

### Dynamic Scheduler
The scheduler feature runs on JavaScript.

### Instant Messaging
The Live Chat feature uses Action Cable to seamlessly integrate WebSockets with the rest of a Rails application. If you aren't familiar with Websocets, it basically allows an open communication session to begin between a browser and a server. This allows the user to send messages to a server and receive responses without having to poll the server for a reply. Action Cable also provides a JavaScript framework for developers which also allowed for easy access to the models of this rails app written with Active Record. 

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
Creating a simple channel for client-server communication

{% highlight erb %}
<% @ta_list.each do |k, v| %>
<li class="online_sym">
  <%= button_to k.first_name + " (#{v})", conversations_path(user_id: k), remote: true, method: :post, class: 'chatlist' %>
</li>
<% if k.online %>
  <li class="online_sym"> <%= render 'partial' %> </li>
<% end %>
<% end %>
{% endhighlight %}


{% highlight ruby %}

{% endhighlight %}



We built the Live Chat feature so it can withstand multiple channels from a single user, allowing someone to hold many private conversations at once.


