**Websocket Application step**

follow the following link for the code and understanding
https://medium.com/@javatechie/build-real-time-notifications-in-spring-boot-applications-websocket-1d5a452c528c

**dependencies**
1. Lombok Developer Tools
2. Spring Boot DevTools Developer Tools
3. Spring Web Web
4. WebSocket Messaging

**Steps**
1. write you code according to the website
2. create your .html file in resources like - src\main\resources\static\messageBox.html
3. run your program and after the run the .html file
4. right-click on the .html(messageBox.html) file -> Browser -> chrome(any browser)

make sure the WebSocketMessageBrokerConfigurer this class is not getting @Override Error but we have to add the following method

```
    @Override
    public void configureMessageBroker(MessageBrokerRegistry config) {
        config.enableSimpleBroker("/topic");  // Prefix for broadcasting messages
        config.setApplicationDestinationPrefixes("/app");  // Prefix for client-to-server communication
    }

    @Override
    public void registerStompEndpoints(StompEndpointRegistry registry) {
        registry.addEndpoint("/ws")  // This is the WebSocket endpoint
                .setAllowedOrigins("http://localhost:63342")  // Allow frontend origin (localhost:63342)
                .withSockJS();  // Enable SockJS for fallback support
    }