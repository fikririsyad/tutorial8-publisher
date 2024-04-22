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