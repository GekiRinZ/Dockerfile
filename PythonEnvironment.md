# Chạy chương trình với environment

1. Cài đặt Virtual Environment
```sh
sudo apt-get install -y python3-venv
```

2. Khởi tạo thư mục chứ Python programming Environment:
```sh
mkdir env
cd env
```

3. Khởi tạo Environment:
```sh
pyvenv env
```
4. Để sử dụng Environment, ta cần active Environment:
```sh
source env/bin/activate
```

--->`(env) silverwolf591997@silverwolf591997-GL62-7RD:~/env$ `

5. Chạy 1 trương trình Hello World trong thư mục:
```sh
(env) silverwolf591997@silverwolf591997-GL62-7RD:~/env$ python helloworld.py
Output:
`Hello, World!`
```

6. Để dừng Environment, sử dụng lệnh `deactivate`
