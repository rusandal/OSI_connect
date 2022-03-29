# Клиент-серверное приложение
## Описание
В составе репозитория имеется 2 программы Клиент и Сервер.  
Клиент отправляет сообщения, сервер принимает и печатает в консоль.  

Клиент:
1. Создается клиентский сокет
```
Socket clientSocket = new Socket(host, port)
```
2. Определяется поток читающий ввод с клавиатуры для последующей отправке на сервер
```
BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
```
3. Выделяем входящие и исходящие потоки клиента
```
PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);
BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()))
```
4. Получение и отправка сообщений
```
serverWord = in.readLine();
System.out.println(serverWord);
String answer = reader.readLine();
out.write(answer + "\n");
out.flush();
```

Сервер:
1. Определяем порт для серверного сокета
```
ServerSocket serverSocket = new ServerSocket(port);
```
2. Ждем подключения от клиента
```
Socket clientSocket = serverSocket.accept();
```
3. Определяем потоки получения и отправки сообщений
```
PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);
BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
```
4. Отправка и получение сообщений
```
out.println("Введите имя");
String username = in.readLine();
```