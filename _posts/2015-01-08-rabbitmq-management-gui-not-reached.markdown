---
author: admin
comments: false
date: 2015-01-08 11:28:35+00:00
layout: post
link: https://witr.net/quotation/?p=669
slug: rabbitmq-management-gui-not-reached
title: RabbitMQ management gui not reached
wordpress_id: 669
categories:
- rabbitMQ
---


if http://server-name:15672 is not reached be sure that you enabled rabbitmq_management


<blockquote>
witr$ rabbitmq-plugins enable rabbitmq_management
</blockquote>


you must **restart RabbitMQ** server, if you wish enabling takes effect


<blockquote>
witr$ service rabbitmq-server restart
</blockquote>




