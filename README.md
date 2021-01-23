C++11 Socket Class
==================

## Creating a Server Socket

```

net::serversocket* server = new net::serversocket(8080);
int err = server->listen();

if (err != 0) {
    std::cerr << strerror(err) << std::endl;
    exit(err);
}

while (true) {
    net::socket* client = server->accept();
    
    if (!client->valid()) {
        delete client;
        continue;
    }
}

```

## Creating a Socket (TCP Client)

```

net::socket* client = new net::socket();
int err = server->listen();

if (server->connect("127.0.0.1", 8002) == CONNECT_ERROR)
    std::cerr << "Problem with connection!\n";

client->send("Hello guys!");

std::cout << client->read() << std::endl;

```