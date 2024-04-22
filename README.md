# Tutorial 8
Fikri Risyad Indratno</br>
2206031170</br>
Advanced Programming B</br>

---

## Reflection
> a. "How much data will your publisher program send to the message broker in one run?"

The program will send five data to the message broker in one run because, in the `main` function, we made five `publish_event` which will send messages to the message broker.

> b. The URL 'amqp://guest:guest@localhost:5672' in the subscriber program is the same as in the publisher program, and what does it mean?

It means that both subscriber and publisher programs are connected to the same message broker.

### Running RabbitMQ as message broker

![running rabbitmq](images/running_rabbitmq.png)

### Sending and processing event

#### Subscriber console
![subscriber console](images/cargo_run_subscriber.png)

#### Publisher Console
![publisher console](images/cargo_run_publisher.png)

When we run subscriber and publisher with `cargo run`, the publisher will send five messages to RabbitMQ, and the subscriber will listen and print all the messages in its console.

### Monitoring chart based on publisher

![repeated publisher run](images/repeated_publisher_run.png)

From the image above, we can see that there are three spikes in the second chart. The first spike shows up when I try to run `cargo run` three times in rapid succession and peaks at 3.0/s, the second and third spikes appear when I try to run `cargo run` two times with a longer interval and both of them peaks at 1.0/s. Based on my observation, the spikes tell us how many messages were running through the system at that current time.

### Simulation slow subscriber

![slow subscriber](images/slow_subscriber.png)

I made the subscriber slower by enforcing it to sleep for every process. The total number of queued messages after running `cargo run` five times is 20, which indicates how many messages are still in the queue at that current time, before they get handled by the subsciber.

### Running at least three subscribers

![three subscribers](images/three_subscribers.png)
![rabbitmq three subscribers](images/rabbitmq_three_subscribers.png)

The spike in the queued messages chart is smaller and decrease quicker. Since there are three subscribers, the message broker can distribute the messages in the queue to all three subscribers at one time making it much faster than only having one subscriber.