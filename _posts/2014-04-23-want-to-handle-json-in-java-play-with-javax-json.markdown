---
author: admin
comments: false
date: 2014-04-23 09:32:10+00:00
layout: post
link: https://witr.net/quotation/?p=702
slug: want-to-handle-json-in-java-play-with-javax-json
title: 'want to handle json in Java : play with javax.json'
wordpress_id: 702
categories:
- java
- json
---



First get libraries
With maven for example add these two artifacts

    
    
            
            <dependency>
                <groupid>javax.json</groupid>
                <artifactid>javax.json-api</artifactid>
                <version>1.0</version>
            </dependency>
    
            
            <dependency>
                <groupid>org.glassfish</groupid>
                <artifactid>javax.json</artifactid>
                <version>1.0.4</version>
            </dependency>
    



Parse json String variable (event processing)

    
    
    
        String json = "{"name":"witr","quotes":{"java":"150","linux":"200"}}";
    
        JsonParserFactory factory = Json.createParserFactory(null);
        JsonParser parser = factory.createParser(new StringReader(json));
    
        while (parser.hasNext()) {
            JsonParser.Event event = parser.next();
    
            switch (event) {
                case KEY_NAME: {
                    String key = parser.getString();
                    System.out.print(key + "="); break;
                }
                case VALUE_STRING: {
                    String value = parser.getString();
                    System.out.println(value); break;
                }
            }
        }
        
        // output :
        // name=witr
        // quotes=java=150
        // linux=200
    




    
    
    
        String json = "{"name":"witr","quotes":{"java":150,"linux":200}}";
    
        JsonReader jsonReader = Json.createReader(new StringReader(json));
        JsonObject jsonObject = jsonReader.readObject();
        System.out.println("name : "+jsonObject.getString("name"));
        System.out.println("quotes : "+jsonObject.getJsonObject("quotes"));
        System.out.println("java : "+jsonObject.getJsonObject("quotes").getInt("java"));
        System.out.println("linux : "+jsonObject.getJsonObject("quotes").getInt("linux"));
    
        // output :
        // name : witr
        // quotes : {"java":150,"linux":200}
        // java : 150
        // linux : 200
    




