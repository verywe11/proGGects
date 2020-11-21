
# Youtube уроки


    int main()
    {
        int n;
        std::cout << "koll-vo"<< std::endl;
        std::cin >> n;
        std::cout << "sobiras est "<< n << " pir"<< std::endl;
        for (int i = n; i >= 1; --i)
      std::cout << "ostalos "<< i << " pir"<< std::endl;
      if(n > 20)
      std::cout << "bad "<< std::endl;
      else
      if(n < 10) 
      std::cout << "goloden "<< std::endl;
      else
      std::cout << "ok "<< std::endl;
    }
    
### Oстаток

    #include <iostream>
    #include <string>
    
    int main()
    {
      int n;
      std::cin >> n;
      int o = n % 100;
      std::cout << o << std::endl;
    }
    
### Switch

    int main()
    {
      std::cout << "koll-vo: " ;
      int n;
      std::cin >> n;
      std::cout << " i sobiras " << n ;
      int o = n % 100;
      if ((o > 10) && (o < 20))
      std::cout << "pir-ov " ;
      else{
          switch(o % 10)
          {
              case 0:
              std::cout << "pir-ov " ;
              break;
              case 1:
              std::cout << "pir-ok " ;
              break;
              case 2:
              case 3:
              case 4:
              std::cout << "pir-ka " ;
              break;
              case 5:
              case 6:
              case 7:
              case 8:
              case 9:
              std::cout << "pir-ov " ;
              break;
    }
    }
    
       std::cout <<  std::endl;
    }
    
### Kалькулятор

    int main()
    {
      float x;
      float y;
      char o;
      char d;
      do {
      std::cout << " figure - operation - figure" << std::endl;
      std::cin >> x;
      std::cin >> o;
      std::cin >> y;
      float r;
          switch(o)
          {
              case '+':
              r = x + y;
              break;
              case '-':
              r = x - y;
              break;
              case '*':
              r = x * y;
              break;
              case '/':
              r = x / y;
              break;
    }
    std::cout << r;
    std::cout << "dalee?";
    std::cin >> d;
    }
    while(d == 'y');
    }
    
### Таблица умножения

    #include <iostream>
    
    int main()
    {
      for (int i = 1; i <= 10; ++i)
      {
      for (int j = 1; j <= 10; ++j)
      std::cout  << i * j << " ";
    std::cout << std::endl;  }}
    
### Комп сам вычисляет угол и макс рассотяние(бросание тела под углом к горизонту)

    #include <iostream>
    #include <cmath>
    
    float dist(float v, float a)
    { return v * v * sin(2 * a * M_PI / 180) / 9.81;}
    
    int main()
    {
      float v;
      float a;
      std::cout << "skorost, m\c: ";
      std::cin >> v;
      //float d = v * v * sin(2 * a * M_PI / 180) / 9.81;
      float d;
      float max_d;
      float max_a;
      max_d = 0;
      for (float a = 0; a < 90; a += 1)
      {d = dist(v,a);
      if (max_d < d)
      { max_d = d;
       max_a = a;}}
      //float d = dist(v, a);
      std::cout << "max, m: "<< max_d << std::endl;
      std::cout << "max ugol, grad: "<< max_a << std::endl;
      }
    
### Численное интегрирование

    #include <iostream>
    #include <cmath>
    
    float dist2(float v, float a)
    { return v * v * sin(2 * a * M_PI / 180) / 9.81;}
    float dist(float v, float a)
    { float x = 0;
    float y = 0;
    float vx = v * cos(a * M_PI / 180);
    float vy = v * sin(a * M_PI / 180);
    float dt = 0.0001;
    while(y >= 0)
    { x += vx * dt;
    y += vy * dt;
    vy -= 9.81 * dt;}
    return x;}
    
    int main()
    { std::cout << dist(10, 45) << std::endl;
    std::cout << dist2(10, 45) << std::endl;
      }
    
### Угадай число

    #include <iostream>
    #include <cstdlib>
    #include <ctime>
    
    int main()
    {  
      srand(time(0));
      bool done;
      do {
      int i = rand() % 100;
      while(true)
      {  std::cout << "kakoe? ";
      int j;
      std::cin >> j;
      if (i > j)
       std::cout << "vverh " << std::endl;
       else
       {if (i < j)
       std::cout << "vniz " << std::endl;
       else
       {std::cout << "OK " << std::endl;
       break;}   }  }
       std::cout << "GO? ";
       char c;
       std::cin >> c;
       done = (c != 'y');
      }while (!done);}
    
### Метод половинного деления

(для быстрого поиска в примере выше начинаем с 100\2 = 50 потом 50\2)

    #include <iostream>
    #include <cstdlib>
    #include <cmath>
    
    float f(float x)
    {
        return x * x  - 2;
        }
    
    float n(float x1, float x2)
    {
        float x = (x2 + x1) / 2;
        while (abs(f(x)) > 0.001)
        {if(f(x) > 0)
        x2 = x;
        else
        x1 = x;
        x = (x2 + x1) / 2;    
        }
        return x;
        }
    
    int main()
    {  
       std::cout << n(0, 100)<< std::endl;
      }
    
### Игра отгадай число для компа

    #include <iostream>
    #include <cstdlib>
    #include <cmath>
    
    float f(float x)
    {
        std::cout << (int)x << std::endl;
        std::cout << "ok? ";
        while(true)
        {
        char c;
        std::cin >> c;
        switch (c){
        case '+': return +1;
        case '-': return -1;
        case '=': return 0;
        }
        std::cout << "bad. "<< std::endl;;
        }
    }
    float n(float x1, float x2)
    {
        float x = (x2 + x1) / 2;
        float y = f(x);
        while (abs(y) > 0.001)
        {if(y > 0)
        x1 = x;
        else
        x2 = x;
        x = (x2 + x1) / 2;    
        y = f(x);
        }
        return x;
        }
    
    int main()
    {  
       std::cout << "figure" << (int)n(0, 100)<< std::endl;
      }

### Пример класса

    #include <iostream>
    #include <string>
    #include <cmath>
    
    class Human
    {
        public:
        int age;
        int weight;
        void print()
        {std::cout << "age: " << age << " weight: " << weight <<std::endl;
        }
    };
    
    
    int main()
    {  
        Human me;
        Human a;
        me.age = 32;
        me.weight = 70;
        a.age = 11;
        a.weight = 22;
        me.print();
        a.print();
      }
    
### Массив с классом

    class A
    { 
        public:
        int x;
        int y;
        };
    
    int main()
    {  
      A a[20];
      for (int i = 0; i < sizeof(a) / sizeof(a[0]); ++i)
      {a[i].x = i * i;
      a[i].y = i;
      }
      
      for (int i = 0; i < sizeof(a) / sizeof(a[0]); ++i)
      std::cout << a[i].x << std::endl;
      }
    
### Двухмерные массивы

    #include <iostream>
    #include <string>
    #include <cmath>
    
    
    
    int main()
    {
        
        const int H = 15;
        const int W = 56;
        char m[15][56];
        for (int y = 0; y < H;++y)
         for (int x = 0; x < W;++x)
         m[y][x] = '.';
        for (int x = 0; x < W;++x)
        {
          //  int y = H - x * x * H / (W * W);
           int y = H - sin(1.0 * x * 2 * M_PI / W + 1) / 2 * H;
        if ((y >= 0) && (y < H))
        m[y][x] = '*';
        }
         for (int y = 0; y < H;++y)
         {
         for (int x = 0; x < W;++x)
         std::cout << m[y][x];
         std::cout << std::endl;
         }
      }
    
### Cортировка

    int main()
    {
        int n = 5;
        int a[n];
        a[0] = 36; // индекс первого элемента - 0 (нулевой элемент)
        a[1] = 27;
        a[2] = 48;
        a[3] = 89;
        a[4] = 10; 
        //ifstream f("C:\\file.txt.txt")
        for (int i = 0; i < n; ++i)
        {
           // std::cin >> a[i];
           // std::cout << a[i] << std::endl;
        }
        for (int i = n - 1; i >= 1; --i)
        for (int j = 0; j < i; ++j)
        {
            if (a[j] > a[j + 1])
            {
                int foo = a[j];
                a[j] = a[j + 1];
                a[j + 1] = foo;
            }
        }
        std::cout  << std::endl;
        for(int i = 0; i < n; ++i)
        std::cout << a[i] << std::endl;
    }
    
### Поиск числа в отсортированном массиве

    int main()
    {
      //fstream f("file.txt");
      //const int n = 100;
     // int m[n];
      int n = 5;
        int m[n];
        m[0] = 36; // индекс первого элемента - 0 (нулевой элемент)
        m[1] = 27;
        m[2] = 48;
        m[3] = 89;
        m[4] = 10; 
      for (int i = 0; i < n; ++i)
      n >> m[i];
      int x;
      std::cout << "vvedite iskomoe ";
      std::cin >> x;
      for (int i = 0; i < n; ++i)
      if (x == m[i])
      {
        std::cout << "chislo " << "nahoditsa " << i;
        break;
          }
    }
    
### Поиск числа в отсортированном массиве 

Метод половинного деления ньютона(работает но криво)

    int main()
    {
      //fstream f("file.txt");
      //const int n = 100;
     // int m[n];
      int n = 6;
        int m[n];
        m[0] = 36; // индекс первого элемента - 0 (нулевой элемент)
        m[1] = 27;
        m[2] = 48;
        m[3] = 89;
        m[4] = 10; 
        m[5] = 11;
      for (int i = 0; i < n; ++i)
      n >> m[i];
      int x;
      std::cout << "vvedite iskomoe ";
      std::cin >> x;
      float l = 0;
      float r = 6;
      float a = (l + r) / 2;
      while ((m[(int)a] != x) && (r - l > 1))
      {if(m[(int)a] < x)
      l = a;
      else
      r = a;
      a = (l + r) / 2;
          }
          std::cout << "chislo " << "nahoditsa " << (int)a;
          }
    
### Vector

    #include <iostream>
    #include <vector>
    #include <string>
    
    int main()
    {
      vector<int> m;
      for (int i = 0; i < 10; ++i)
      m.push_back(i);
      for (int i = 0; i < m.size(); ++i)
      std::cout << m[i]<< std::endl;
    //for (int i = 0; i < m.size(); ++i)
     // m[i] = m[i] * m[i];
     // std::cout << std::endl;
     // for (int i = 0; i < m.size(); ++i)
     // std::cout << m[i]<< std::endl;
    }
    
### Телефонная книга

    #include <iostream>
    #include <vector>
    #include <fstream>
    #include <string>
    
    class Number
    {
    public:
    	string name;
    	string number;
    	Number(const Number &v):
    	name(v.name),
    		number(v.number){}
    	Number(){}
    	const number &operator=(const Number &v)
    	{
    	name = v.name;
    	number = v.number;
    	return v;
    	}
    };
    
    int main()
    {
      fstream f("file.txt");
      vector<Number> telBook;
      while(true)
      {
       Number t;
       f >> t.name
    	   if(f.eof())
    		   break;
       f >> t.number
    	   if(f.eof())
    		   break;
       telBook.push_back(t);
      }
       while(true)
       {
    	   std::cout << "vvedite name(or stop)";
    	string name;
    	std::cin >> name;
    	if (name == "stop")
    		break;
    	for(int i = 0; i < telBook.size(); ++i)
    	{
    		if(telBook[i].name == name)
    		{
    			std::cout << name << telBook[i].namber << std::endl;
    		}
    	}
       }
    
### Школьный метод нахождения числа пи

    int main()
    {
    	float p = 0;
    	float z = 1;
    	for(int i = 1; i < 100000; i+=2)
    	{
    	p += z * 4 / i;
    	z *= -1;
    	}
    	return p;
    }
    
### Немного об Open gl

    #include <iostream>
    #include <GL/glut.h> // это не библиотека open GL, это наДстройка над ней, позволяет на любой ОС исп ее
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); // все сотрем
    	glBegin(GL_POINTS); // так рисуем точки
    	//glBegin(GL_LINES);  // так рисуем линию
    	glColor3f(0.0, 0.0, 0.0); // черный
    	// êкрасный, зеленый, синий 1.0 будет значить добавление цвета
    	//glColor3f(1.0, 0.0, 0.0); /
    	glVertax2f(0.25, 0.25);// чтобы поставить точку // 2 означает координату x,y - f =float
    	// glVertax2f(0.75, 0.75);
    	// glColor3f(0.0, 1.0, 0.0); /
    	// glVertax2f(0.75, 0.25); // вторая линия, начало
    	// glVertax2f(0.25, 0.75); // вторая линия конец
    	// glColor3f(0.0, 0.0, 1.0); /
    	// glVertax2f(0.50, 0.25); 
    	// glVertax2f(0.50, 0.75); 
    	glEnd(); // когда нарисуем нужное кол-во
    	glFlush(); // перенос всего нарисованного на окно(чтобы увидеть)
    
    }
    
    int main(int argc, char **argv) // задаем пары которые м\б переданы в программу, чтобы эти пары передать в глут
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); //  пары экрана, которые будут у OGL, 
    			//SINGLE означает, что будем 1 буфер исп //RGB означает, что будем исп 24xбитный цвет(по 8 на каждый)
    	glutInitWindowSize(240, 240);
    	glutInitWindowPosition(100, 740);
    	glutCreateWindow("Test"); // команда на создание окна
    	glClearColor(1.0, 1.0, 1.0, 1.0);  // фоновый цвет
    	glMatrixMode(GL_PROJECTION); // для рисования в трехмерном, нужно настроить вид(трехмерн это частный случай
    								//двухмерного, настроим как двухмерный
    	glLoadIdentity();
    	glOrtho(0.0, 1.0, 0.0, 1.0, -1.0, 1.0);
    	glutDisplayFunc(display);
    	glutDisplayFunc(display); // функция, которая будет все рисовать
    	glutMainLoop();// в основной цикл, который будет опрашивать клаву, мышь, перерисовывать все, изменять размеры экрана
    }
    
### Долгое бросание монеты

    #include "stdafx.h"
    #include <iostream>
    #include <GL/glut.h> // 
    #include <cstdlib>
    
    const int SER_COUNT = 240;
    int r()
    {
    int r = 0;
    for (int i = 0; i < SER_COUNT; ++i)
    {
    	if (rand() % 2)
    		r++;
    	return r;
    }
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	int q[SER_COUNT + 1];
    	for (int i = 0; i <= SER_COUNT; ++i)
    		q[i] = 0;
    	for(int i = 0; i < 10000; ++i)
    		q[r()]++;
    		int max = 0;
    	for (int i = 0; i <= SER_COUNT; ++i)	
    		if(max < q[i])
    			max < q[i];
    	glBegin(GL_POINTS);
    	glColor3f(0.0, 0.0, 0.0);
    	for(int i = 0; i <= SER_COUNT; ++i)
    		glVertex2f(i, SER_COUNT * q[i] / max);
    	glEND();
    	glFlush(); //
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); //
    	glutInitWindowSize(240, 240);
    	glutInitWindowPosition(100, 740);
    	glutCreateWindow("Coin"); //
    	glClearColor(1.0, 1.0, 1.0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0.0, 240.0, 0.0, 240.0, -1.0, 1.0);
    	glutDisplayFunc(display);// 
    	glutMainLoop();/
    }
    

### Pекурсия

    #include <cstdlib>
    
    //int f(int n) // факториал, в обратную сторону?
    //{if(n == 1)
    //return 1;
    //else 
    //return f(n - 1) * n;}
    void t(int r, int b, int e)
    {
    	int c;
    	if (b == 1) && (e == 2) || (b == 2) && (e == 1)))
    		c = 3;
    	else
    	if (b == 1) && (e == 3) || (b == 3) && (e == 1)))
    		c = 2;
    	else
    	if (b == 2) && (e == 3) || (b == 3) && (e == 2)))
    		c = 1;
    	if (r > 1)
    	{
    	t(r - 1, b, c);
    	std::cout << b << " -> " << e << std::endl;;
    	t(r - 1, c, e);
    	}
    	else 
    		std::cout << b << " -> " << e << std::endl;;
    }
    
    int main() 
    {
    	t(1, 1, 3);
    	//t(2, 1, 3);
    	//t(3, 1, 3);
    }
    

### Cалфетка

    #include <cstdlib>
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glColor3f(0.0, 0.0, 0.0); 
    	glBegin(GL_LINES);
    	enum {N = 3}; // 4-5-6-20
    	for (int i = 0; i < N; ++i)
    		for (int j = i + 1; i < N; ++i)
    		{
    		glVertex2f (cos(2 * M_PI * i / N),
    				sin(i2 * M_PI * i / N));
    		glVertex2f (cos(2 * M_PI * j / N),
    				sin(i2 * M_PI * j / N));
    		}
    	glEnd();
    	glFlush();
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); //
    	glutInitWindowSize(240, 240);
    	glutInitWindowPosition(100, 740);
    	glutCreateWindow(""); //
    	glClearColor(1.0, 1.0, 1.0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(-1.0, 1.0, -1.0, 1.0, -1.0, 1.0);
    	glutDisplayFunc(display);// 
    	glutMainLoop();/
    }
    
### Pекурсия (не бьющие дрд квины)
    #include <cstdlib>
    
    int board[8][8];
    
    void setQueen(int i, int j)
    {
    for (int x = 0; x < 8; ++x)
    {
    ++board[x][j];
    ++board[i][x];
    int foo;
    foo = j - i + x;
    if (foo >= 0 && foo < 8
    	++board[x][foo];
    if (foo >= 0 && foo < 8
    	++board[x][foo];
    }
    board[i][j] = -1;
    }
    
    void resetQueen(int i, int j)
    {
    for (int x = 0; x < 8; ++x)
    {
    --board[x][j];
    --board[i][x];
    int foo;
    foo = j - i + x;
    if (foo >= 0 && foo < 8
    	--board[x][foo];
    if (foo >= 0 && foo < 8
    	--board[x][foo];
    }
    board[i][j] = 0;
    }
    
    bool tryQueen(int i)
    {
    	bool result = false;
    	for (int j = 0; j < 8; ++j)
    	{
    	if (board[i][j] == 0)
    		setQueen(i, j);
    	if (i == 7) 
    		result == true;
    	else
    	{
    	if (!(result = tryQueen(i + 1)))
    	resetQueen(i,j);
    	}
    	}
    	if (result)
    		break;
    }
    return result;
    }
    
    int main() 
    {
    	for (int i = 0; i < 8; ++i)
    		for (int j = 0; j < 8; ++j)
    			board[i][j] == 0)
    			tryQueen(0);
    	for (int i = 0; i < 8; ++i)
    		for (int j = 0; j < 8; ++j)
    		{
    		if (board[i][j] = -1)
    			std::cout << "[]";
    		else
    		std::cout << "."
    		}
    std::cout << std::endl;
    }
    
### Разбор арифм выражений(калькулятор)

    #include <cstdlib>
    
    float number()
    {
    	int res = 0;
    	for(;;)
    	{
    		char c = std::cin.get();
    		if(c >= '0' && c <= '9')
    		{
    		res = res * 10 + c - '0';
    		else
    		{
    			std::cin.putback(c);
    			break;
    		}
    		}
    		return res;
    	}
    float expr();
    float factor()
    {
    	float x;
    char c = std::cin.get();
    if (c == '(')
    {
    x = expr();
    std::cin.get();
    else
    {
    std::cin.putback(c);
    x = number();
    }
    }
    
    c = std::cin.get();
    switch(c)
    {
    case '*':
    	return x * factor();
    case '/':
    	return x / factor();
    default:
    	std::cin.putback(c);
    	return x;
    }
    }
    
    float expr()
    {
    float x = factor();
    char c = std::cin.get();
    switch(c)
    {
    case '+':
    	return x + expr();
    case '-':
    	return x - expr();
    	default:
    	std::cin.putback(c);
    	return x;
    }
    }
    
    int main() 
    {	
    std::cout << "vvedite ";
    float r = expr();// factor
    std::cout << "res " << r << std::endl;
    }
    
    
### Исправленный калькулятор(беск циклы)

    #include <cstdlib>
    
    float number()
    {
    	int res = 0;
    	for(;;)
    	{
    		char c = std::cin.get();
    		if(c >= '0' && c <= '9')
    		
    		res = res * 10 + c - '0';
    		else
    		{
    			std::cin.putback(c);
    			
    		return res;
    		}
    	}
    
    float skobki()
    {
    char c = std::cin.get();
    if (c == '(')
    {
    float x = expr();
    std::cin.get();
    return x;
    }
    else{
    std::cin.putback(c);
    return number();
    }
    }
    
    float expr();
    
    float factor()
    {
    	float x = skobki();
    	for(;;)
    	{
    char c = std::cin.get();
    switch (c)
    
    {
    case '*':
    	x *= skobki();
    	break;
    case '/':
    	x /= skobki();
    	break;
    default:
    	std::cin.putback(c);
    	return x;
    }}
    }
    
    float expr()
    {
    	float x = factor();
    	for(;;)
    	{
    char c = std::cin.get();
    switch (c)
    
    {
    case '+':
    	x += factor();
    	break;
    case '-':
    	x -= factor();
    	break;
    default:
    	std::cin.putback(c);
    	return x;
    }}
    }
    
    int main() 
    {
    std::cout << "vvedite ";
    float res = expr();// factor
    std::cout << "res " << res << std::endl;
    }
    
### Вращающийся куб

    #include <GL/glut.h> 
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glRotatef(1, 1, 1, 0);
    	glBegin(GL_LINE_STRIP);
    	glVertex3f(-50, -50, -50);
    	glVertex3f(50, -50, -50);
    	glVertex3f(50, 50, -50);
    	glVertex3f(-50, 50, -50);
    	glVertex3f(-50, -50, -50);
    	glEnd(); 
    	glBegin(GL_LINE_STRIP);
    	glVertex3f(-50, -50, 50);
    	glVertex3f(50, -50, 50);
    	glVertex3f(50, 50, 50);
    	glVertex3f(-50, 50, 50);
    	glVertex3f(-50, -50, 50);
    	glEnd();
    	glBegin(GL_LINES);
    	glVertex3f(-50, -50, 50);
    	glVertex3f(-50, -50, -50);
    	glVertex3f(50, -50, 50);
    	glVertex3f(50, -50, -50);
    	glVertex3f(50, 50, 50);
    	glVertex3f(50, 50, -50);
    	glVertex3f(-50, 50, 50);
    	glVertex3f(-50, 50, -50);
    	glEnd();
    	glFlush(); 
    
    void timer(int = 0)
    {
    displat();
    glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); 
    	glutInitWindowSize(200, 200);
    	glutInitWindowPosition(20, 810);
    	glutCreateWindow("Cube");
    	glClearColor(0, 0, 0, 1.0);  
    	glMatrixMode(GL_PROJECTION); 
    	glLoadIdentity();
    	glOrtho(-100, 100, -100, 100, -100, 100);
    	glutDisplayFunc(display);
    	timer();
    	glutMainLoop();/
    }
    std::cout << "vvedite ";
    float res = expr();// factor
    std::cout << "res " << res << std::endl;
    }
    
### Программа печатает саму себя

    #include <iostream>
    string s = "\";\nvoid r(string &s, char c, string str)\n {size_t p = 0; \n while ((p = s.find(c, p) != string::npos) \n{s = s.substr(0, p) + str + s.substr(p + 1); p += str.size(); } }\nint main() \n{	string z = s;	\nr(z, '\\\\', \"\\\\\\\\\"); 	r(z, '\\n', \"\\\\n\"); 	r(z, '\"' "\\\\\\\"\");	\nstd::cout << \"#include <iostream>\\n string s = \\\"\"; << z << s";} \n";
    
    void r(string &s, char c, string str)
    {
    size_t p = 0;
    while ((p = s.find(c, p) != string::npos)
    {s = s.substr(0, p) + str + s.substr(p + 1); p += str.size(); }
    }
    
    int main() 
    {
    	string z = s;
    	r(z, '\\', "\\\\"); 	r(z, '\n', "\\n"); 	r(z, '"' "\\\"");
    	std::cout << "#include <iostream>\n string s = ""; << z << s";
    }
       



### Cпецэффект

    #include <GL/glut.h>
    #include <vica.h> // image, method saves image for langvij C++
    #include <cstdlib>
    #include <cmath>
    
    //auto create
    static const unsigned int width = 200;
    static const unsigned int height = 200;
    #define HEADER_PIXEL(data,pixel) {\
    	pixel[0] = (((data[0] - 33) << 2) | ((data[1] - 33) >> 4)); \
    	pixel[1] = ((((data[1] - 33) & 0xF) << 4) | ((data[2] - 33) >> 2)); // dalee
    \
    	pixel[2] = ((((data[2] - 33) & 0x3) << 6) | ((data[3] - 33))); \
    	data += 4; \
    }
    static const char *header_data = "...."
    //auto create
    
    
    typedef float Color[3];
    struct Pixel
    {
    float x;
    float y;
    int x0;
    int y0;
    Color color;
    };
    Pixel bitmap[height] [wigth];
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glBegin(GL_POINTS);
    	for (int y = 0; y < height; ++y)
    	for (int x = 0; x < width; ++x)
    	{
    		Pixel &p = bitmap[y][x];
    		glColor3f(p.color[0], p.color[1], p.color[2]);
    		glVertex2f(p.x, p.y);
    		float d = sqrt((p.x0 - p.x) * (p.x0 - p.x) + 
    			(p.y0 - p.y) * (p.y0 - p.y))
    			if (d > 0.1)
    			{
    			p.x += 0.1 * (p.x0 - p.x) / d;
    			p.y += 0.1 * (p.y0 - p.y) / d;
    			}
    			else
    			{
    			p.x = p.x0;
    			p.y = p.y0;
    			}
    	}
    		glEnd();
    	glutSwapBuffers();
    }
    
    void timer(int = 0)
    {
    	display();
    	glutTimerFunc(1, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	const char *d = header_data;
    	Color pixel;
    	for (int y = 0; y < height; ++y)
    	for (int x = 0; x < width; ++x)
    	{
    	HEADER_PIXEL(d, pixel);
    	Pixel &p = bitmap[y][x];
    	p.color[0] = pixel[0] / 255.0;
    	p.color[1] = pixel[1] / 255.0;
    	p.color[2] = pixel[2] / 255.0;
    	p.x0 = x;
    	p.y0 = y;
    	p.x = rand() % width;
    	p.y = rand() % heigth;
    	}
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(200, 200);
    	glutInitWindowPosition(20, 810);
    	glutCreateWindow("Spec-effect"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0, 200, 200, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	timer();
    	glutMainLoop();/
    }
    
### Моделирование гравитации

    #include <GL/glut.h>
    #include <cmath>
    
    struct Particle
    {
    float x;
    float y;
    float vx;
    float vy;
    float m;
    }
    
    const int N = 4;
    Particle particle[N];
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glBegin(GL_POINTS);
    	for(int i = 0; i < N; ++i)
    	glVertex2f(particles[i].x, particles[i]. y);
    		glEnd();
    	glutSwapBuffers();
    }
    	void timer(int = 0)
    {
    	for(int i = 0; i < N; ++i)
    	{
    	Particle &p0 = particles[i];
    	for(int j = 0; j < N; ++j)
    	{
    	if (j == i)
    		continue;
    	const Particle &p = particles[j];
    	float d = sqrt((p0.x - p.x) * (p0.x - p.x) +
    		(p0.y - p.y) * (p0.y - p.y));
    	if (d > 3)
    	{
    	p0.vx += 0.0007 * p.m / d / d * (p.x - p0.x) / d;
    	p0.vy += 0.0007 * p.m / d / d * (p.y - p0.y) / d;
    	}
    	}
    	p0.x += p0.vx;
    	p0.y += p0.vy;
    	}
    	display();
    	glutTimerFunc(1, timer, 0);
    }
    }
    
    int main(int argc, char **argv) // 
    {
    	particles[0].x = 100;
    	particles[0].y = 100;
    	particles[0].vx = 0;
    	particles[0].vy = 0;
    	particles[0].m = 1000;
    
    	particles[1].x = 130;
    	particles[1].y = 100;
    	particles[1].vx = 0;
    	particles[1].vy = -0.1;
    	particles[1].m = 7;
    
    	particles[2].x = 30;
    	particles[2].y = 100;
    	particles[2].vx = 0;
    	particles[2].vy = 0.1;
    	particles[2].m = 10;
    
    	particles[3].x = 25;
    	particles[3].y = 100;
    	particles[3].vx = 0;
    	particles[3].vy = 0.11;
    	particles[3].m = 0.1;
    
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); //
    	glutInitWindowSize(200, 200);
    	glutInitWindowPosition(20, 810);
    	glutCreateWindow("gravitation"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(-0, 200, 200, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	timer();
    	glutMainLoop();/
    }
    
### Рисуем фрактал

    #include <iostream>
    #include <GL/glut.h>
    #include <cmath>
    
    class Complex
    {
    public:
    	double re;
    	double im;
    	Complex(double are, double aim): re(are), im(aim) {}
    	Complex operator+(const Complex &v)
    	{
    	return Complex(re + v.re, im + v.im);
    	}
    };
    
    Complex sxr(const Complex &v)
    {
    return Complex(v.re * v.re - v.im * v.im, 2 * v.re * v.im);
    }
    
    double abs(const Complex &v)
    {
    return sqrt(v.re * v.re + v.im * v.im);
    }
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glBegin(GL_POINTS);
    	for(int y = 0; y < 200; ++y)
    		for(int x = 0; x < 200; ++x)
    		{
    		Complex z(0,0);
    		int i = 0;
    		while(i < 1000 && abs(z) < 2)
    		{
    		z = sqr(z) + Complex(1.0 * (x - 100) / 70,
    			                    1/0 * (y - 100) / 70)
    			++i;
    		}
    		if (abs(z) >= 2)
    		{
    		float col = (50.0 - i) / 50/0;
    		glColor3f(col, col, col);
    		glVertex(x, y);
    		}
    		}
    		glEnd();
    	glutSwapBuffers();
    }
    	void timer(int = 0)
    {
    	display();
    	glutTimerFunc(1, timer, 0);
    	//utochnit
    }
    
    int main(int argc, char **argv) // 
    {
    //utochnit
    }
    
### 4асы

    #include <iostream>
    #include <GL/glut.h>
    #include <cmath>
    #include <ctime>
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glBegin(GL_LINES);
    	for(int i = 0; i < 12; ++i)
    	{
    		float x = sin(2 * M_PI / 12 * i);
    		float y = cos(2 * M_PI / 12 * i);
    		glVertex2f(400 * x, 400 * y);
    		glVertex2f(380 * x, 380 * y);
    	}
    	time_t t = time(0);
    	tm *lt = localtime(&t);
    	int h = lt -> tm_hour;
    	int m = lt -> tm_min;
    	int s = lt -> tm_sec;
    	float x = sin(2 * M_PI * (h * 60 + m) / 12 / 60);
    	float y = cos(2 * M_PI * (h * 60 + m) / 12 / 60);
    	glVertex2f(0, 0);
    	glVertex2f(200 * x, 200 * y);
    	x = sin(2 * M_PI * m / 60);
    	y = cos(2 * M_PI * m / 60);
    	glVertex2f(0, 0);
    	glVertex2f(350 * x, 350 * y);
    	x = sin(2 * M_PI * s / 60);
    	y = cos(2 * M_PI * s / 60);
    	glVertex2f(0, 0);
    	glVertex2f(380 * x, 380 * y);
    	glEnd();
    	glutSwapBuffers();
    	
    }
    	void timer(int = 0)
    {
    	display();
    	glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(400, 400);
    	glutInitWindowPosition(20, 1050 - 480 - 20);
    	glutCreateWindow("Clock"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(-400, 400, -400, 400, -400, 400);
    	glutDisplayFunc(display);// 
    	timer();
    	glutMainLoop();/
    }
    
### Рисование в полярных координатах

    #include <cmath>
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glColor3f(0.0, 0.0, 0.0);
    	glBegin(GL_LINE_LOOP);
    	for(float a = 0; a < 2 * M_PI; a += 0.01)
    	{
    	//float r = 0.2 * (1 + sin(a)) * (1 + 0.9 * cos(8 * a)) * 
    	//	(1 + 0.1 * cos(24 * a));
    	//glVertex2f(r * cos(a), r * sin(a)); //ahahhahahh
    	}
    	// for(float a = 0; a < 100 * 2 * M_PI; a += 0.01)
    	glVertex2f(cos(a), sin(a));
    	// glVertex2f(cos(a), sin(2.1 * a + 2));
    	//glVertex2f(cos(a), sin(5.1 * a + 2));
    	glEnd();
    	glFlush();
    	
    }
    	void timer(int = 0)
    {
    	display();
    	glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); //
    	glutInitWindowSize(240, 240);
    	glutInitWindowPosition(100, 740);
    	glutCreateWindow("Drawing in polar coordinates"); //
    	glClearColor(1.0, 1.0, 1.0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(-1.0, 1.0, -1.0, 1.0, -1.0, 1.0);
    	glutDisplayFunc(display);// 
    	glutMainLoop();/
    }
    
### Кит и кот

    #include <iostream>
    #include <string>
    #include <vector>
    using namespace std;
    
    struct Node 
    {
    	Node(): yes(-1), no(-1) {}
    string q;
    int yes;
    int no;
    };
    
    int main() 
    {
    vector<Node> tree;
    Node n;
    n.q = 'kit';
    tree.push_back(n);
    for(;;)
    {
    int i = 0;
    while (tree[i].yes != -1 && tree[i].no != -1)
    {
    	cout << tree[i].q << "? (1 - da, 0 - net) ";
    	int ans;
    	cin >> ans;
    	if (ans == 1)
    		i = tree[i].yes;
    	else
    	i = tree[i].no;
    }
    cout << " this is " << tree[i].q << "? (1 - da, 0 - net) ";
    	int ans;
    	cin >> ans;
    	if (ans == 1)
    	cout << "ugadali " << endl;
    	else
    	{
    		cout << "kto? ";
    		string anim;
    		cin >> anim;
    		cout << " differens " << tree[i].q << "from " << anim << "? ";
    		string diff;
    		cin >> diff;
    		Node yes = tree[i];
    		Node no;
    		no.q = anim;
    		tree[i].yes = tree.size();
    		tree.push_back(yes);
    		tree[i].no = tree.size();
    		tree.push_back(no);
    		tree[i].q = diff;
    
    	}
    	cout << "dalee? (1 - da, 0 - net) ";
    	cin >> ans;
    	if (ans == 0)
    		break;
    
    }
    }
    
### Моделирование груза на пружине

    #include <GL/glut.h>
    #include <cmath>
    #include <string>
    
    struct Load
    {
    float y;
    float vy;
    };
    
    Load load = { 350, 0};
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glBegin(GL_LINES);	
    	glVertex2f(200, 0);
    	glVertex2f(200, load y);
    	for(int i = 0; i < 36; ++i)
    	{
    	glVertex2f(200 + 5 * cos(2 * M_PI * i / 36), load.y + 5 * sin(2 * M_PI * i / 36));
    	glVertex2f(200 + 5 * cos(2 * M_PI * (i + 1) / 36), load.y + 5 * sin(2 * M_PI * (i + 1) / 36));
    	}
    	glEnd();
    	glutSwapBuffers();
    
    	void timer(int = 0)
    {
    	float f;
    	if (load.y > 200)
    		f = 0.001 * (load.y - 200);
    	f -= 0.1;
    	load.vy -= f;
    	load.y += load.vy;
    	display();
    	glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char *argv[]) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(400, 400);
    	glutInitWindowPosition(20, 1050 - 450);
    	glutCreateWindow("Load"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(-0, 400, 400, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	timer();
    	glutMainLoop();/
    }
    
### Моделирование резинки

    #include <GL/glut.h>
    #include <cmath>
    #include <string>
    #include <vector>
    
    const int DELTA_T = 10000; //
    
    struct Particle
    {
    float x;
    float y;
    float vx;
    float vy;
    };
    
    class Rubber
    {
    	vector<Particle> P_;
    public:
    	Rubber()
    	{
    	const int N = 20;
    	for (int i = 0; i < N; ++i)
    		Particle tmp = { 200 + i * 200 / N, i * 20 / N, 0, 0}
    	p_.push_back(tmp);
    	}
    	void draw() const
    	{
    	glBegin(GL_LINE_STRIP);
    	for (vector<Particle>::const_iterator i = p_.begin(); i != p_.end(); ++i)
    		glVertex2f(i -> x, i -> y);
    		glEnd();
    		glBegin(GL_LINE_STRIP);
    		cost Particle &p = *p_.rbegin();
    		for (int i =0; i < 36; ++i)
    			glVertex2f(p.x + 5 * cos(2 * M_PI * i / 36), p.y + 5 * sin(2 * M_PI * i / 36)
    		glEnd();
    	}
    	void tick()
    	{
    	for (int i = 1; i < p_.size(); ++i)
    	{
    	float ax = 0;
    	float ay = 0;
    	float a = 0;
    	Particle &p0 = p_[i - 1];
    	Particle &p1 = p_[i];
    
    	float d = sqrt((p1.x - p0.x) * (p1.x - p0.x) + (p1.y - p0.y) * (p1.y - p0.y)
    		const float rest = 180.0 / p_.size();
    		if (d > rest)
    			a = 0.3 * (d - rest);
    		if (d < 2)
    			a = 1E-0 * (2 - d);
    	ax = a * (p0.x - p1.x) / d;
    	ay = a * (p0.y - p1.y) / d;
    	p1.vx += ax * DELTA_T / 1000000.0;
    	p1.vx += ax * DELTA_T / 1000000.0;
    	if (i != 1)
    	{
    	p0.vx += ax * DELTA_T / 1000000.0;
    	p0.vy += ay * DELTA_T / 1000000.0;
    	}
    	}
    	Particle &p = *p_.rbegin();
    	p.vy += 1E-2;
    	for (vector<Particle>::iterator i = p_.begin(); i != p_.end(); ++i)
    	{
    	i -> vx *= (1 - 1E-4);
    	i -> vy *= (1 - 1E-4);
    	i -> x += i -> vx * DELTA_T / 1000000.0;
    	i -> y += i -> vy * DELTA_T / 1000000.0;
    	}
    
    };
    
    Rubber rubber;
    
    Load load = { 350, 0};
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT); 
    	glutSwapBuffers();
    }
    
    	void timer(int = 0)
    {
    	for(int i = 0; i < 200000 / DELTA_; ++i)
    		rubber.tick();
    	display();
    	glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(400, 400);
    	glutInitWindowPosition(20, 1050 - 480 - 20);
    	glutCreateWindow("Rubber band"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0, 400, 400, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	timer();
    	glutMainLoop();/
    }
    
### Обход конем

    #include <iostream>
    #include <GL/glut.h>
    #include <cmath>
    #include <string>
    #include <vector>
    
    const int N = 8;
    bool board[N][N];
    struct Position
    {
    int x;
    int y;
    };
    vector<position> solution;
    
    void display()
    {
    	static int c = 0;
    	++c;
    	if(c % 5000 != 0)
    	return;
    	glClear(GL_COLOR_BUFFER_BIT); 
    	const int step = 480 / N;
    		glBegin(GL_QUADS);
    	for(int i = 0; i < N; ++i)
    		for(int j = 0; j < N; ++j)
    	{
    		if (( i + j) % 2)
    			glColor3f(0.5, 0.5, 0.5);
    		else
    			glColor3f(0, 0, 0);
    	const int x = i * step;
    	const int y = j * step;
    	glVertex2f(x, y);
    	glVertex2f(x + step, y);
    	glVertex2f(x + step, y + step);
    	glVertex2f(x, y + step);
    	}
    	glEnd();
    	
    	glBegin(GL_QUADS);
    	for(int i = 0; i < N; ++i)
    		for(int j = 0; j < N; ++j)
    	{
    		if (( i + j) % 2)
    			glColor3f(0.5, 0.5, 0.5);
    		else
    			glColor3f(0, 0, 0);
    	const int x = i * step;
    	const int y = j * step;
    	glVertex2f(x, y);
    	glVertex2f(x + step, y);
    	glVertex2f(x + step, y + step);
    	glVertex2f(x, y + step);
    	}
    	glEnd();
    
    	glPointSize(3);
    	glBegin(GL_POINTS);
    	glColor3f(0, 1, 0);
    	for(int i = 0; i < N; ++i)
    		for(int j = 0; j < N; ++j)
    	if (bord[i][j])
    	{
    		const int x = i * step + step / 2;
    		const int y = j * step + step / 2;
    		glVertex2f(x, y);
    	}
    	glEnd();
    	glPointSize(1);	
    	glBegin(GL_LINE_STRIP);
    	for(vector<Position>::iterator i = solution.begin(); i != solution.end(); ++i)
    	{
    		const int x = i -> step + step / 2;
    		const int y = j -> * y step + step / 2;
    		glVertex2f(x, y);
    	}
    	glEnd();
    	glutSwapBuffers();
    }
    
    bool solve(int x, int y)
    {
    	board[x][y] = true;
    	Position tmp = {x, y};
    	solution.push_back(tmp);
    	display();
    	if (solution.size() == N * N)
    		return true;
    
    	const struct
    	{
    	int dx;
    	int dy;
    	}moves[] =
    	{
    		{-1, -2},
    		{1, -2},
    		{-2, -1},
    		{2, -1},
    		{-2, 1},
    		{2, 1},
    		{-1, 2},
    		{1, 2}
    	};
    	for (int i = 0; i < sizeof(moves) / sizeof(*moves); ++i)
    	{
    	const int x0 = x + moves[i].x;
    	const int y0 = y + moves[i].y;
    	if (x0 >= 0 && x0 < N && 
    		y0 >= 0 && y0 < N && 
    		!board[x0][y0] &&
    		solve(x0, y0)
    		return true;
    	}
    
    	board[x][y] = false;
    	slusion.pop_back();
    	return false;
    }
    
    	void timer(int = 0)
    {
    	for(int i = 0; i < N; ++i)
    	for(int j = 0; j < N; ++j)
    	bord[i][j] = false;
    	solution.clear();
    
    	solve(0, 0);
    	//display();
    	//glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(480, 480);
    	glutInitWindowPosition(20, 1050 - 480);
    	glutCreateWindow("Knigth's tour"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0, 480, 480, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	glutTimeFunc(10, timer, 0);
    	board[4][4] = true;
    	//Position tmp1 = {4, 4};
    	//solution.push_back(tmp1); // proverka risovania doski
    	//Position tmp2 = {4, 7};
    	//solution.push_back(tmp2);
    	glutMainLoop();
    
### Обход конем улучш

    #include <iostream>
    #include <GL/glut.h>
    #include <cmath>
    #include <string>
    #include <vector>
    #include <map>
    
    const int N = 50;
    bool board[N][N];
    struct Position
    {
    int x;
    int y;
    };
    vector<position> solution;
    
    void display()
    {
    	static int c = 0;
    	++c;
    	if(c % 5000 != 0)
    	return;
    	glClear(GL_COLOR_BUFFER_BIT); 
    	const int step = 480 / N;
    		glBegin(GL_QUADS);
    	for(int i = 0; i < N; ++i)
    		for(int j = 0; j < N; ++j)
    	{
    		if (( i + j) % 2)
    			glColor3f(0.5, 0.5, 0.5);
    		else
    			glColor3f(0, 0, 0);
    	const int x = i * step;
    	const int y = j * step;
    	glVertex2f(x, y);
    	glVertex2f(x + step, y);
    	glVertex2f(x + step, y + step);
    	glVertex2f(x, y + step);
    	}
    	glEnd();
    	
    	glBegin(GL_QUADS);
    	for(int i = 0; i < N; ++i)
    		for(int j = 0; j < N; ++j)
    	{
    		if (( i + j) % 2)
    			glColor3f(0.5, 0.5, 0.5);
    		else
    			glColor3f(0, 0, 0);
    	const int x = i * step;
    	const int y = j * step;
    	glVertex2f(x, y);
    	glVertex2f(x + step, y);
    	glVertex2f(x + step, y + step);
    	glVertex2f(x, y + step);
    	}
    	glEnd();
    
    	glPointSize(3);
    	glBegin(GL_POINTS);
    	glColor3f(0, 1, 0);
    	for(int i = 0; i < N; ++i)
    		for(int j = 0; j < N; ++j)
    	if (bord[i][j])
    	{
    		const int x = i * step + step / 2;
    		const int y = j * step + step / 2;
    		glVertex2f(x, y);
    	}
    	glEnd();
    	glPointSize(1);	
    	glBegin(GL_LINE_STRIP);
    	for(vector<Position>::iterator i = solution.begin(); i != solution.end(); ++i)
    	{
    		const int x = i -> step + step / 2;
    		const int y = j -> * y step + step / 2;
    		glVertex2f(x, y);
    	}
    	glEnd();
    	glutSwapBuffers();
    }
    
    bool solve(int x, int y)
    {
    	board[x][y] = true;
    	Position tmp = {x, y};
    	solution.push_back(tmp);
    	display();
    	if (solution.size() == N * N)
    		return true;
    
    	const struct
    	{
    	int dx;
    	int dy;
    	}moves[] =
    	{
    		{-1, -2},
    		{1, -2},
    		{-2, -1},
    		{2, -1},
    		{-2, 1},
    		{2, 1},
    		{-1, 2},
    		{1, 2}
    	};
    	multimap<int, int> seq;
    	for (int i = 0; i < sizeof(moves) / sizeof(*moves); ++i)
    	{
    	const int x0 = x + moves[i].x;
    	const int y0 = y + moves[i].y;
    	int c = 0;
    	for (int j = 0; j < sizeof(moves) / sizeof(*moves); ++j)
    	{
    	const int x1 = x0 + moves[j].x;
    	const int y1 = y0 + moves[j].y;
    	if (x1 >= 0 && x1 < N && 
    		y1 >= 0 && y1 < N && 
    		!board[x1][y1])
    		++c;
    	}
    	seq.insert(pair<int, int>(c, i));
    	}
    	for (multimap<int, int>::iterator i = seq.begin(); i != seq.end(); ++i)
    	{
    	const int x0 = x + moves[i -> second].x;
    	const int y0 = y + moves[i -> second].y;
    	if (x0 >= 0 && x0 < N && 
    		y0 >= 0 && y0 < N && 
    		!board[x0][y0] &&
    		solve(x0, y0)
    		return true;
    	}
    
    	board[x][y] = false;
    	slusion.pop_back();
    	return false;
    }
    
    	void timer(int = 0)
    {
    	for(int i = 0; i < N; ++i)
    	for(int j = 0; j < N; ++j)
    	bord[i][j] = false;
    	solution.clear();
    
    	solve(0, 0);
    	//display();
    	//glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(480, 480);
    	glutInitWindowPosition(20, 1050 - 480);
    	glutCreateWindow("Knigth's tour"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0, 480, 480, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	glutTimeFunc(10, timer, 0);
    	board[4][4] = true;
    	//Position tmp1 = {4, 4};
    	//solution.push_back(tmp1); // proverka risovania doski
    	//Position tmp2 = {4, 7};
    	//solution.push_back(tmp2);
    	glutMainLoop();
    }
    
### Волновой алгоритм

    #include <cstdlib>
    #include <algorithm>
    
    const int N = 24;
    const int WALL = 9999;
    int map[N][N];
    vector<pair<int, int>> wave;
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT);
    	glBegin(GL_QUADS);
    	for(int i = 0; i < N; ++i)
    		for (int j = 0; j < N; ++j)
    		{
    			if(map[i][j] == WALL)
    			glColor3f(1, 1, 1);
    			else if (map[i][j] == -1)
    				glColor3f(0, 0, 0);
    			else 
    				glColor3f(map[i][j] / 48.0, 0, 0);
    	glVertex2f((i) * 480 / N, (j) * 480 / N);
    	glVertex2f((i + 1) * 480 / N, (j) * 480 / N);
    	glVertex2f((i + 1) * 480 / N, (j + 1) * 480 / N);
    	glVertex2f((i) * 480 / N, (j + 1) * 480 / N);
    		}
    		for (vector<pair<int, int>> :: iterator i = wave.begin(); i != wave.end(); ++i)
    			{
    			glColor3f(0, 1, 0);
    			glVertex2f((i -> first) * 480 / N, (i -> second) * 480 / N);
    			glVertex2f((i -> first) * 480 / N, (i -> second) * 480 / N);
    			glVertex2f((i -> first) * 480 / N, (i -> second) * 480 / N);
    			glVertex2f((i -> first) / N, (i -> second) * 480 / N);
    	glEnd();
    	glutSwapBuffers();
    }
    
    	void timer(int = 0)
    {
    	for (int i = 0; i < N; ++i)
    		for (int j = 0; j < N; ++j)
    		{
    			if (rand() % 4 == 0)
    			map[i][j] = WALL;
    			else
    				map[i][j] = -1;
    		}
    		for(int i = 0; i < N; ++i)
    		{
    			map[i][0] = WALL;
    			map[0][i] = WALL;
    			map[i][N - 1] = WALL;
    			map[N -1][i] = WALL;
    
    		}
    		vector<pair<int, int>> oldWave;
    		oldWave.push_back(pair<int, int>(1, 1));
    		int nstep = 0;
    		map[1][1] = nstep;
    		const int dx[] = {0, 1, 0, -1};
    		const int dy[] = {-1, 0, 1, 0};
    		while (oldWave.size() > 0)
    		{
    			++nstep;
    			wave.clear();
    			for (vector<pair<int, int>> :: iterator i = oldWave.begin(); i != oldWave.end(); ++i)
    			{
    			for (int d = 0; d < 4; ++d)
    			{
    				int nx = i -> first + dx[d];
    				int ny = i -> second + dy[d];
    				if (map[nx][ny] == -1)
    				{
    				wave.push_back(pair<int, int>(nx, ny));
    				map[nx][ny] = nstep;
    				display();
    				if(nx == N - 2 && ny == N - 2)
    					goto done;
    				for(int b = 0; b < 10000; ++b)
    				{}
    				}
    			}
    			}
    			oldWave = wave;
    		}
    done:
    	int x = N - 2;
    	int y = N - 2;
    	wave.clear();
    	wave.push_back(pair<int, int>(x, y));
    	while (map[x][y] != 0)
    	{
    	for (int d = 0; d < 4; ++d)
    	{
    	int nx = x + dx[d];
    	int ny = y + dy[d];
    	if(map[x][y] - 1 == map[nx][ny])
    	{
    	x = nx;
    	y = ny;
    	wave.push_back(pair<int, int>(x, y));
    	break;
    	}
    	}
    	}
    	display();
    	//glutTimerFunc(10, timer, 0);
    }
    
    int main(int argc, char **argv) // 
    {
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(480, 480);
    	glutInitWindowPosition(20, 1050 - 480);
    	glutCreateWindow("Sample Algorithm"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0, 480, 480, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	glutTimeFunc(10, timer, 0);
    	glutMainLoop();
    }
    
### Броуновское движение

    #include <GL/glut.h>
    #include <cmath>
    #include <string>
    #include <vector>
    #include <map>
    #include <cstdlib>
    #include <algorithm>
    
    const float DT = 0.01;
    
    struck P
    {
    float x;
    float y;
    float vx;
    float vy;
    float m;
    };
    
    vector<P> p;
    
    void display()
    {
    	glClear(GL_COLOR_BUFFER_BIT);
    	for (vector<P>::iteraor i = p.begin(); i != p.end(); ++i)
    	{
    	if (i -> = <= 2)
    		glPointSize(2);
    	glBegin(GL_POINTS);
    	glVertex2f(i -> x, i -> y);
    	glEnd();
    	}
    	else
    	{
    		glBegin(GL_LINES);
    	for (int a = 0; a < 36; ++a)
    	{
    		float x = i -> m * cos(a * M_PI / 18);
    		float y = i -> m * sin(a * M_PI / 18);
    		glVertex2f(i -> x + x, i -> y + y);
    		x = i -> m * cos((a + 1) * M_PI / 18);
    		y = i -> m * sin((a + 1) * M_PI / 18);
    		glVertex2f(i -> x + x, i -> y + y);
    	}
    	glEnd();
    	}
    	
    	glutSwapBuffers();
    }
    
    	void timer(int = 0)
    {
    	//for (int i = 0; i < N; ++i)
    	
    	for (vector<P>::iteraor i = p.begin(); i != p.end(); ++i)
    		for (vector<P>::iteraor j = p.begin(); j != p.end(); ++j)
    		if (i != j)
    		{
    		float d = sqrt((i -> x - j -> x) * (i -> x - j -> x) + (i -> y - j -> y) * (i -> y - j -> y))
    			if(d < i -> m + j -> m)
    			{
    			float f = 50 *(i -> m + j -> m - d);
    			i -> vx += f * (i -> x - j -> x) / d / i -> m * DT;
    			i -> vx += f * (i -> y - j -> y) / d / i -> m * DT;
    			j -> vx -= f * (i -> x - j -> x) / d / j -> m * DT;
    			j -> vx -= f * (i -> y - j -> y) / d / j -> m * DT;
    			}
    		}
    		for (vector<P>::iteraor i = p.begin(); i != p.end(); ++i)
    		{
    		i -> x += i -> vx * DT; 
    		i -> y += i -> vy * DT; 
    		if (i -> x < 0)
    			i -> x += 480;
    		if(i -> y < 0)
    			i -> y += 480;
    		if(i -> x > 480)
    			i -> x -= 480;
    		if(i -> y > 480)
    			i -> y -= 480;
    		display();
    		glutTimerFunc(10, timer, 0);
    		}
    }
    
    int main(int argc, char **argv) // 
    {
    	P p = {480 / 2, 480 / 2, 0 , 0, 40}
    	p.push_back(p0);
    	for (int i = 0; i < 100; ++i)
    	{
    		P p = {rand() % 480, rand() % 480, rand() % 100000 / 500/0 - 100, rand() % 100000 / 500/0 - 100, 1 }
    		p.push_back(p0);
    	}
    	glutInit(&argc, argv);
    	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB); //
    	glutInitWindowSize(480, 480);
    	glutInitWindowPosition(20, 1050 - 480);
    	glutCreateWindow("Sample Algorithm"); //
    	glClearColor(0, 0, 0, 1.0);  // 
    	glMatrixMode(GL_PROJECTION); // 
    	glLoadIdentity();
    	glOrtho(0, 480, 480, 0, -1, 1);
    	glutDisplayFunc(display);// 
    	glutTimeFunc(10, timer, 0);
    	timer();
    	glutMainLoop();
    }
    
### стек

    #include <iostream>
    #include <string>
    #include <fstream>
    #include <Windows.h>
    #include <cstring>
    
    using namespace std;
    
    class Msg
    {
    public:
      Msg(){}
      Msg(string ms) :m_ms(ms) {}
        void Print() {
            cout <<  m_ms << endl;
        }
    private:
        string m_ms;
    };
    
    int main()
    {
        fstream fs("myfile.txt");
        if (!fs) {
            cout << "ups\n"; //
            return 1;
        }
        string msg;
    	SetConsoleOutputCP(1251);
        while(getline(fs, msg)) //
        {
            if (msg.length() > 100) {
                Msg m(msg); // 
                m.Print(); /
                }
        }
    	int mmm;
    	cin >> mmm;
    }
    
    
### Запись в файл простейшая

    #include <iostream>
    #include <string>
    #include <fstream>
    using namespace std;
    
    int main()
    {
    	
    	ofstream fout;
    	fout.open("myfile.txt");
    	
    	if(!fout.is_open())
    	{
    	cout << "OSHIBKA " << endl;
    	}
    	else
    	{
    	fout << 555;
    	}
    	fout.close();
    }
    
    
### Запись в файл с циклом

    #include <iostream>
    #include <string>
    #include <fstream>
    using namespace std;
    
    int main()
    {
    	ofstream fout;
    	fout.open("myfile.txt", ofstream::app);
    	
    	if(!fout.is_open())
    	{
    	cout << "OSHIBKA " << endl;
    	}
    	else
    	{
    		for(int i = 0; i < 5; i++)
    		{
    		cout << "vvedite " << endl;
    		int a;
    		cin >> a;
    		fout << a;
    		fout << "\n";
    		}
    	}
    	fout.close();
    }
    
### Чтение из файла посимвольно

    #include <iostream>
    #include <string>
    #include <fstream>
    using namespace std;
    
    int main()
    {
    	ifstream fin;
    	fin.open("myfile.txt");
    	if (!fin.is_open())
    	{
    	cout << "oshibka " << endl;
    	}
    else
    {
    cout << "Otktito " << endl;
    char ch;
    	while(fin.get(ch))
    	{
    	cout << ch;
    	}
    fin.close();
    }
    	int n;
    	cin >> n;
    }
    
### Чтение из файла построчно

    #include "stdafx.h"
    #include <iostream>
    #include <string>
    #include <fstream>
    #include <Windows.h>
    using namespace std;
    
    int main()
    {
    	SetConsoleOutputCP(1251);
    	ifstream fin;
    	fin.open("myfile.txt");
    	if (!fin.is_open())
    	{
    	cout << "oshibka " << endl;
    	}
    else
    {
    cout << "Otktito " << endl;
    string str;
    
    while(!fin.eof())
    {
    getline(fin, str);
    	//fin >> str;
    cout << str << endl;
    }
    fin.close();
    }
    	int n;
    	cin >> n;
    }
    
### Запись класса в файл

    Point point(414, 4244, 424);
    
    	ofstream fout;
    	fout.open("myfile.txt", ofstream::app);
    	if(!fout.is_open())
    	{
    	cout << "OSHIBKA " << endl;
    	}
    	else
    	{
    		cout << "Otktito " << endl;
    		fout.write((char*)&point, sizeof(Point));
    	}
    	fout.close();
    
### Чтение из файла с пом класса

    #include <iostream>
    #include <string>
    #include <fstream>
    #include <Windows.h>
    using namespace std;
    
    class Point
    {
    public:
    Point()
    {
    x = y = z = 0;
    }
    Point(int x, int y, int z)
    {
    this->x = x;
    this->y = y;
    this->z = z;
    }
    	void Print()
    	{
    		cout << "x: " << x << " y: " << y << " z: " << z << endl;
    	}
    	int x;
    	int y;
    	int z;
    };
    
    int main()
    {
    	SetConsoleOutputCP(1251);
    
    	ifstream fin;
    	fin.open("myfile.txt");
    	if (!fin.is_open())
    	{
    	cout << "oshibka " << endl;
    	}
    else
    	{
    	cout << "Otktito " << endl;
    	Point pnt;
    	while(fin.read((char*)&pnt, sizeof(Point)))
    	{
    	pnt.Print();
    	}
    	}
    	fin.close();
    	int m;
    	cin >> m;
    }
    
### Чтение и запись из файла

    #include <iostream>
    #include <string>
    #include <fstream>
    #include <Windows.h>
    using namespace std;
    
    int main()
    {
    	fstream fs;
    	fs.open("myfile.txt", fstream::in | fstream::out | fstream::app);
    	if (!fs.is_open())
    	{
    	cout << "oshibka " << endl;
    	}
    	else
    	{
    		string msg;
    		int value;
    	cout << "Otktito " << endl;
    	cout << "1 dla zapisi " << endl;
    	cout << "2 dla chtenia " << endl;
    	cin >> value;
    	
    	if(value == 1)
    	{
    	cout  << "vvedite sms " << endl;
    	SetConsoleCP(1251);
    	cin >> msg;
    	fs << msg << "\n";
    	SetConsoleCP(866);
    	}
    	if(value == 2)
    	{
    	while(!fs.eof())
    	{
    	//msg = 
    		fs >> msg;
    		cout << msg << endl;
    	}
    	}
    	fs.close();
    	int n;
    	cin >> n;
    	}
    }
    
### Считать строку из файла

    #include <iostream>
    #include <string>
    #include <fstream>
    #include <Windows.h>
    using namespace std;
    
    int main()
    {
    	fstream fs;
    	fs.open("myfile.txt", fstream::in | fstream::out | fstream::app);
    
    	if (!fs.is_open())
    	{
    	cout << "oshibka " << endl;
    	}
    	else
    	{
    		string msg;
    		int value;
    	cout << "Otktito " << endl;
    	cout << "1 dla zapisi " << endl;
    	cout << "2 dla chtenia " << endl;
    	cin >> value;
    	
    	if(value == 1)
    	{
    	cout  << "vvedite sms " << endl;
    	//
    	cin >> msg;
    	fs << msg << "\n";
    	//SetConsoleOutputCP(866);
    	}
    	if(value == 2)
    	{
    	for (int i = 0; i < 2; i++)
    	{
    		SetConsoleOutputCP(1251);
    		getline(fs, msg);
    		//fs >> msg;
    		cout << msg << " ";
    	}
    	}
    	fs.close();
    	int n;
    	cin >> n;
    	}
    }
    
### Сортировка пузырьком

    #include <fstream>
    #include <Windows.h>
    using namespace std;
    
    int main()
    {
    	const int n = 5;
    	int a[n];
        ifstream f("myfile.txt");
        for (int i = 0; i < n; ++i)
        {
           f >> a[i];
    	   cout << a[i] << endl;
        }
        for (int i = n - 1; i >= 1; --i)
        for (int j = 0; j < i; ++j)
        {
            if (a[j] > a[j + 1])
            {
                int foo = a[j];
                a[j] = a[j + 1];
                a[j + 1] = foo;
            }
        }
        cout << endl;
        for(int i = 0; i < n; ++i)
        cout << a[i] << endl;
    	int b;
    	cin >> b;
    }
    
### Не прокатила быстрая сортировка

    void sort(vector<int> &v, int b0, int e0)
    {
    	int d = v[e0];
    	int b = b0;
    	int e = e0;
    	do
    	{
    	while (v[b] < d)
    		++b;
    	while (v[e] < d)
    		--e;
    	if(b <= e)
    	{
    	swap(v[b], v[e]);
    	++b;
    	++e;
    	}
    	}while (b <= e);
    	if(e > b0)
    		sort(v, b0, e);
    	if(b > e0)
    		sort(v, b, e0);
    }
    
    void deggree()
    {
    vector<int> v;
    	for(int i = 0; i < 20; ++i)
    		v.push_back(i);
    	for(size_t i = 0; i < v.size(); ++i)
    		swap(v[i], v[rand() % (v.size() - i) + i]);
    }
    
    int main()
    {
    
    std::for_each(v.begin(), v.end(), (int i) -> void {cout << i};		
    }
    
## стек (copy)

    #include <iostream>
    #include <string>
    #include <fstream>
    #include <Windows.h>
    #include <cstring>
    
    using namespace std;
    
    class Msg
    {
    public:
      Msg(){}
      Msg(string ms) :m_ms(ms) {}
        void Print() {
            cout <<  m_ms << endl;
        }
    private:
        string m_ms;
    };
    
    int main()
    {
        fstream fs("myfile.txt");
        if (!fs) {
            cout << "ups\n";
            return 1;
        }
        string msg;
    	SetConsoleOutputCP(1251);
        while(getline(fs, msg))
        {
            if (msg.length() > 100) { 
                Msg m(msg); 
                m.Print(); 
            }
        }
    	int mmm;
    	cin >> mmm;
    }
    
### Стек + поиск слова с заменой и выводом строки после слова

    #include <string>
    #include <fstream>
    #include <Windows.h>
    #include <cstring>
    #include <vector>
    #include <sstream>
    
    using namespace std;
    
    string rla(istream& stream, const string& what) 
    {
        for (string word; stream >> word;) {
            if (word == what) {
                string line;
                getline(stream, line);
                return line;
            }
        }
        return "";
    }
    
    class Msg
    {
    public:
      Msg(){}
      Msg(string ms) :m_ms(ms) {}
        void Print() {
            cout <<  m_ms  << endl;
    		 cout << endl;
        }
    	void Pri() {
    		
    	stringstream stream(m_ms);
    	cout << rla(stream, "abyssal");
        }
    
    private:
        string m_ms;
    };
    
    int main()
    {
        fstream fs("myfile.txt");
        string msg;
    	SetConsoleOutputCP(1251);
    	
        while(getline(fs, msg)) 
        {
    		switch(msg.length())
    		{
    		  case 104:{Msg m(msg); m.Pri();}
    		
    		}
        }
    	int mmm;
    	cin >> mmm;
    }
    
### Stack - Последнее за 2409
    #include <vector>
    #include <sstream>
    
    using namespace std;
    
    string rla(istream& stream, const string& what) 
    {
    	for(int i = 0; i < 10; ++i)
    	{ 
        for (string word; stream >> word;) {
            if (word == what) {
                string line;
                getline(stream, line);
    			
    			//cout << m_ms << endl; // razobrat
                return line;
            }
        }
    	}
        return "";
    }
    
    class Msg
    {
    public:
      Msg(){}
      Msg(string ms) :m_ms(ms) {}
      string m_ms;
        void Print() {
            cout <<  m_ms  << endl;
    		 cout << endl;
        }
    	void Pri() {
    	stringstream stream(m_ms);
    	cout << rla(stream, "n");
        }
    
    //private:
        //string m_ms;
    };
    
    int main()
    {
        fstream fs("myfile.txt");
        string msg;
    	SetConsoleOutputCP(1251);
    	
        while(getline(fs, msg)) 
        {
    		switch(msg.length())
    		{
    		  //case 104:{Msg m(msg); m.Pri();}
    		  case 180:{Msg m(msg); m.Pri();} 
    		}
        }
    	int mmm;
    	cin >> mmm;
    }
    
# Timofey

Терн ОП(?:) c ? x : y если с != 0(true), то вычисл x, иначе y. Операнды условного Опа д\б выраж( не стейтами).

    If (x > y) larger = x;
    else larger = y;  
    или larger = (x > y) ? x : y; 
    (*p).b  == p → b

за l-value стоит реальная память. Возвращать адрес лок пер вне Ф-ии нельзя. Имя пер это всегда разыменованный адрес.
C-style строки это Мс char

### 1

сравнение питона с С++, немного про go to, сравнение for и while 
Однопроходные алгоритмы(подсчет за 1 проход)
1 count += 1      2 sum s += x      3 product    p *= x   и пр. - (обычно не нужно запоминать пер)

    m = max(m, x)  //новый максимум равен максимуму из старого максимума и икса   
    →
    int max(int x, int y)   //  можно записать так, 
     if (x > y) retutrn x; 
    return y;
    →
      if ( x > m)   m =  x   //   но обычно записывают так

### 2

двоичный код и кодировки, для вычислений лучше исп int8_t.
Битовые операции

    x = 2;
    y = 5; // меняем местами так
    tmp = x; // новая пер
    x = y;
    y = tmp;
    
    flag = false;
    int x;
    cin x;
    while(x != 0)
    
    if(x%10 == 7)
    Flag = true;
    
    // Тоже, только без if
    Flag = (x%10 == 7) || flag
    

### 3

дробные числа 1 с фикс точкой 2 с плав точкой

### 4

 Функциональные языки кэшируют результаты функций.
Чистые функции получают пары и возвр знач. Они не занимаются вводом\выводом.
(*b) взятие адреса   -    int* тип.

    Struct S { // создаем новый тип S
    int a;
    int b;};
    
    S return_S(int x){ // у функции возвр тип явл-ся S(как int, это созданный тип)
    S result;     //  Но чтобы его вернуть, нужно заготовить локально
    result.a = x * x; // и разложить в его поля значения 
    result.b = x + 2;
    return result; // возвращаем
    
    int main() { // далее структура м\б принята и распакована здесь
    
    
    Int x;
    cin >> x;
    S y = return_S(x); // рассчитывается по x 
    cout << y.a << y.b;
    
    S x, y;
    x.a = 2;
    x.b = 3;
    y = x;
    
    Void modify_pair(t_Pair *p) // структура передана по адресу
    {p->a += 1; // (*p. a   =  p это адрес структуры, его нужно разыменовать, а потом обратится по его атрибуту.
    p->b += 10;}
     
    main() {
     t_Pair x;
    cin >> x.a >> x.b;
    
    t_pair y;
    y = x; // копия сделана в одно действие
    modify_pair(& x); // передаем адрес структуры x
    cout << x.a << x.b;
    cout << y.a << y.b;

Массив A[0], A[1], A[2]
 A                  *       ↔  p
обращение по адресу А(доступ к первому эл по адресу всего Мса. Имя Мса яв-ся почти индексом его начала

     int A[10]
    int* p = &(A[0]) → &A → A   // int* p   указатель на эл
    Имя Мса яв-ся почти адресом его начала
    int* p; // за указателем p стоит ячейка памяти(l-value) в которую м\скопировать сам адрес А, а скопировав
    p = A; // его → м\разыменовать p и положить 
    *p = 10; туда что-либо
    cout << A[0] => 10 // положили в A[0] знач 10
    p = p + 1; // магия
    *p = 20;
    cout << A[1] => 20
    
    *(p + 1) = 20  <=> A[1] = 20 <=> 
    *(p + i) = 20  <=>
    A[i] = 20
    *(p + I) = p[i]; // сместиться на I ячеек вперед(отриц назад) и потом разыменовать — это то же, что сделать p[i].
    *(A + I) = A[i];
    

создаем неизвестный n размер, который возьмем с клавы 

    int n;
    cin >> n; // скажут для скольки чисел в пределе н\создать «решето»
    bool sieve[n + 1] // включительно n + 1
    //предположим что все числа сначала простые → true
    for(int I = 2; I < n + 1; i++) // по всему мс по n + 1 Не включительно
    sieve[i] = true; // ставим везде true
    int x; // переменная по которой идем/ индекс, который соотв числу    
                    sieve[x] // bool т. е. Да или нет
    while(x*x ,= n) // пока не вышел за границы // идем вперед, но если x не  подходит, то он не записывается.
    Для каждого x говорим
    if(sieve[x]) // если решето говорит, что это число x яв-ся true — т. е. простое(не зачеркнуто), значит оставим его простым, и начиная с числа x во 2ой степени идем до конца при пом пер y.
    for(int y = x*x; y <= n; y += x) // включая n, и y увеличим каждый раз на x и зачеркиваем y — присв false
    sieve[y] = false;
    x += 1;
    // сделали решето, осталась мука, которую соберем
    for(int I = 2; I < n + 1; i++)
    if(sieve[i]) // cout только если решето говорит, что I true, выводим само I
    cout << I;

### 5

    int N = 5;
    int A[N] = {1,2,3,4,5}; // как скопировать знач из мса А в В
    int B[N]; // B не l-value, а B это имя мса, т. е. Он превращается в адрес начала мса, без []
    можно скопировать циклом
    for(int I = 0; I < n; ++i)
    B[i] = A[i]; →   B[i] = A[N – I – 1]  // делаем зеркально [I] ↔ [N – I – 1];
    для реверса делаем доп пер tmp
    for(..) tmp = A[N – I – 1];
    A[N – I – 1] = A[i];
    A[i] = tmp;
    
    int x;
    cin >> x; // введем x и заполним ими Мс
    while(x != 0)
    A[top++] = x; // в первый раз top = 0, и 
    cin >> x; // это будет индекс эла
    [top++] = x; // обращение к старому x, а затем увеличение top.
    Пока A не пуст, а за его размер отвечает top
    while(top > 0)
    cout << A[--top];
    - -top // сначала нужно не знач top, а знач [top – 1], а еще нужно уменьшить top на 1. итого – top, уменьшим top и получим знач [top-1]
    

##### Сортировка дурака

    int N = 5;
        int A[N] = {5, 4, 3, 2, 1};   
    
        int i = 0;
        while (i < N-1)
        {
            if (A[i] > A[i+1]) {
                int tmp = A[i];
                A[i] = A[i+1];
                A[i+1] = tmp;
                i = 0;
            } else {
                i += 1;
            }
       }
    
        for(int i = 0; i < N; ++i) {
            cout << A[i] << '\t';    }

##### Сортировка пузырьком

    int N = 5;
        int A[N] = {1, 3, 2, 5, 4};
        bool is_sorted = false;
        while (not is_sorted) {
            int i = 0;
            is_sorted = true;
            while (i < N-1)  {
                if (A[i] > A[i+1]) {
                    int tmp = A[i];
                    A[i] = A[i+1];
                    A[i+1] = tmp;
                    is_sorted = false;
                }
                i += 1;
            }
        }
        for(int i = 0; i < N; ++i) {
            cout << A[i] << '\t';   }

##### проверка на отсортированность мса

    bool is_sorted = true; // предположим, что отсортиван
    for(int I = 0; I < n - 1; ++i) // идем с 0го по n – 1(смотрим на пары n[i] и n[i + 1] N – 1 ограничение, чтобы не выйти за пределы мс. Заменим for на while
    int I = 0;
    while (I < N – 1){
    if (A[i] > A[i + 1]  // < значит все норм, а нам интересно, когда хоть 1 раз не норм. Поэтому
    is_sorted  = false; 
    break;
    cout << s_sorted; // выведет 1 или 0
    //Если нужно исправлять не правильное положение элов тогда break не нужен, и is_sorted тоже не нужно
    тогда int tmp = A[i];
    A[i] = A[i + 1];
    A[i + 1] = tmp;
    I = 0; // когда есть беспорядок — начинай сначала(поэтому отказались от for, чтобы менять пер I сбрасывая ее)
    else I += 1;

и вывод через for()cout << A[i];
можно сортировать не полностью

### 6

указатели

    int x = 5;
    int* px = &x; // почти для любого типа, м\создать ячейку хранящую в себе значение этого типа. Значит, м\создать ячейку типа int* назвать ее px и положить туда = адрес x

Для доступа к 5и м\исп само имя x - (имя пер в «каком-то смысле» всегда итак разыменованный ее адрес).

##### Структура

    struct node_t{
    int data;
    node_t *next; };
    
    void go_through(node_t *p){ // не будем перезаписывать, адрес передан по знач(не изменим ту пер, которая передана, м\менять пар p и не волноваться что тот p сотрется) не н\писать *p_begin
    while(p != nullptr) {  // пока по нему м\обратиться
    cout << (*p).data; // сами адреса не интересны, а интересно то, что по адресу p → структура → data
    p = p->next; // переходим к след звену, есть p — адрес на звено, помещаем в ячейку, хранящую звено, кладем тот адрес, который хранится в самом звене. Разыменовываем, достаем само звено, у него достаем его свойство next — так подменили себе адрес, стали указывать на новое звено
    
    int main() {
    node_t A[5];
    
    for(int I = 0; I < 5; i++){
    A[i].data = I + 1;// разыменование и взятие адреса взаимоуничтож
    A[i].next = &(*(A+0) → A[0] → A →  итого A + I + 1
    Берем адрес I + 1 ячейки, поскольку А это адресный тип — получим смещение от начала Мс на I + 1 ячеек
    A[4].next = nullptr;
    node_t *p_begin = A; // н\иметь указатель на начало
    go_through(p_begin) // чтобы не потерять указатель на начало, создадим копию указ или вызовем Ф-ю, которой даем указ
    
     node_t A[5];
        for(int i = 0; i < 5; i++) {
            A[i].data = i+1;
            A[i].next = A + i + 1;
        }
        A[4].next = nullptr;
        node_t *p_begin = A;
        go_through(p_begin);
    
    node_t *p_begin = new node_t;
        node_t *p = p_begin;
        for(int i = 0; i < 5; i++) {
            p->data = i+1;
            p->next = new node_t; //создаем
            p = p->next;
        }
        p->data = 777;
        p->next = nullptr;
    
        go_through(p_begin);

### 7 пропустил двухмерные Мсы.

### 8

Простейший поиск в Мсе — линейный
что нужно вернуть? 
Наличие - true\false
или само число – место(индекс) отриц число или >= N

    int A[N];
    int x;
    cin >> x;
    int find(int A[], int N, int x) // мс, размер, искомое число
    int index = -1; // специально отриц число или >= N
    for(int i = 0; i < N; i++){
     if(A[i] == x) {
    index = I; // празднуем, зафиксировали место, где его нашли
    break; // если н\вернуть индекс 1го эла или -1 при отсутствии // есть более короткий способ return I — необязательно присв в индекс, и в этом случае можно спросить, а зачем вообще тогда пер index, если доходим до конца, то всегда нужно вернуть -1
    }}
    return index; // return – 1;
    минус — если искомое число встретится более 1го раза. Обычно ищут хоть какое-нить число 2, но какое вернуть?
    
    Int left_bound(int a[], int N, int x){
    int left = -1; // a[left] < x && A[right] >= x – это инвариант цикла, т. е. В любом случае правда
    int right = N; // недопустимый индекс, поэтому до него
    while(right – left > 1) { // в какой-то момент они будут не больше 1го
    int middle = (left – right) / 2; отбрасываем лево\право
    if(A[middle] < x) // если меньше x,
    left = middle; // то подходит в качестве левой границы 
    else 
    right = middle; // а иначе, подходишь в качестве правой границы
    return left; // ради этого все затевалось, находим левую границу

Вопрос: есть или нет число в Мсе?

1) Нет, если left.bound = -1
2) Нет, если по  left.bound = 1

    int find(int A[], int N, int x){
    int left = left_bound(A, N, x); // найдем left при пом ф-ии left_bound передав ей свои пары, и она сделат поиск бинарно
    int Pfi = left + 1; 
    if(Pfi < N && A[Pfi] == x) //  Pfi < N приналежит разумным И ...
    return Pfi;
    else return – 1;

##### Бинарная сортировка

    int left_bound(int A[], int N, int x){
        int left = -1;  // A[left] < x
        int right = N;  // A[right] >= x
        while (right - left > 1) {
            int middle = (left + right) / 2;
            if (A[middle] < x)
                left = middle;
            else
                right = middle;
        }    
        return left;
    }
    
    int find(int A[], int N, int x){
        int left = left_bound(A, N, x);
        int potential_first_index_of_x_in_A = left + 1;
        if (potential_first_index_of_x_in_A < N and 
            A[potential_first_index_of_x_in_A] == x)
            return potential_first_index_of_x_in_A;
        else
            return -1; // x not found
    }
    
    int main(){
        int N = 10;
        int A[] = {1, 3, 3, 7, 7, 7, 7, 9, 10, 10};
        int x;
    
        for(int i = 0; i < N; i++)
        cout << A[i] << '\t';
        cout << '\n';
        cin >> x;
      cout << "left bound x: " << left_bound(A, N, x) << '\n';
    }

##### Сортировка подсчетом

    void count_sort(int A[], int N){
        // н\знать диапазон сортируемых чисел (считаю, что они от 0 до 9)
        int F[10] = {0, 0, 0, 0, 0, 0, 0, 0, 0, 0};
        for(int i = 0; i < N; i++) {
            F[A[i]]++;
        }
        int i = 0;
        for(int x = 0; x < 10; x++) {  // перебираю всевозможные значения ключа! (их M штук)
            for(int k = 0; k < F[x]; k++) {
                A[i] = x;
                i++;
            }
        }
    }
    void generate_random_array(int A[], int N, int M){
        for(int i = 0; i < N; i++)
            A[i] = rand() % M;
    }
    
    void print_array(int A[], int N){
        for(int i = 0; i < N; i++)
            cout << A[i] << '\t';
        cout << '\n';
    }
    int main(){
        int N = 10;
        int A[N];
    
        generate_random_array(A, N, 10);
        print_array(A, N);
        count_sort(A, N);
        print_array(A, N);    }

Не нужно сортировать если ищем 1 раз.
Сортировка подсчетом O(N +M) скрытая ассимптотика от кол-ва потенциальных ключей. Зависит от диапозона, иногда допустимо для текстовых данных.

    void count_sort(int A[], int N){
        // н\знать диапазон сортируемых чисел (считаю, что они от 0 до 9)
        int F[10] = {0, 0, 0, 0, 0, 0, 0, 0, 0, 0}; // массив частот повторений
        for(int i = 0; i < N; i++) { // идем по всем числам
            F[A[i]]++; // собираем частоты, для каждого  A[i], его счетчик ++
        } // передаем в нужные места
        int i = 0; // чтобы знать куда передать
        for(int x = 0; x < 10; x++) {  // перебираю всевозможные значения ключа! (их M штук)
            for(int k = 0; k < F[x]; k++) { // сколько раз этот ключ(х) передаем в A[i], столько, сколько раз он встречался в
    исходном Мсе, а это кол-во хранится в F[x] → k < F[x]
                A[i++] = x; // k раз будет происходить это действие
           //    далее можно написать так            i++; или просто дописать ++ туда
            }
        }
    }
    void generate_random_array(int A[], int N, int M){    for(int i = 0; i < N; i++)        A[i] = rand() % M;}
    
    int main(){      generate_random_array(A, N, 10); // числа от 0 до 10 не вкл
        print_array(A, N); // потом распечатаем
        count_sort(A, N);
        print_array(A, N);   // и снова }

##### поразрядная сортировка

    void radix_sort(int *A, int N)
    {
     int *a0 = new int[N]; //  N штук, не экономим память
     int *a1 = new int[N];
     
     for(int radix = 0; radix < 32; radix++) { // делаем с разрядами до 32х
     int a0_size = 0; // раскладываем по этим 2м
     int a1_size = 0; // по 2м
     for(int i = 0; i < N; i++) { // на две кучи 
     if ((A[i] & (1 << radix)) == 0) // & битовое И с единицой сдвиутой влево на radix(где radix кол-во разрядов)
    и получаем нужный бит из a[i], затем сравниваем с нулем, и если 0
     a0[a0_size++] = A[i]; // в нулевую
     else
     a1[a1_size++] = A[i]; // в первую
     } // в кучки разложено, теперь соеденяем все, сначала разложим кучку A[0], а потом A[1]
     for(int i = 0; i < a0_size; i++) //  i < a0_size чтобы не выйти за границы заполненного уровня 1й кучки
     A[i] = a0[i]; // перебросали 1ю кучку из a0 в A
     for(int i = 0; i < a1_size; i++) // перебросали 2ю кучку из a1 в A, в конец
     A[a0_size + i] = a1[i]; // кладем не в A[i], а по уровню заполненности, который остался после a0_size + i
     }
     delete[] a0; 
     delete[] a1;
    }
    
    void generate_random_array(int A[], int N, int M){
     for(int i = 0; i < N; i++)
     A[i] = rand() % M;
    }
    void print_array(int A[], int N){
        for(int i = 0; i < N; i++)
            cout << A[i] << '\t';
        cout << '\n';
    }
    int main(){
        int N = 10;
        int A[N];
    
        generate_random_array(A, N, 1000);
        print_array(A, N);
        radix_sort(A, N);
        print_array(A, N);}

### 9

Рекурсия — способ решения задачи, через сведение ее к подзадаче(ам), аналогичной(ым) исходной, но проще
дед → бабка → внучка → жучка → мышка ← крайний случай(базовый)
рекурентные случаи(рекурсивный)
1Прямой ход рекурсии(когда функция вызывает саму себя) от деда к мышке, важно чтобы рекурсия начала раскручиваться в обратную сторону(в том числе подразумеваемые вычисления)
2Обратный ход рекурсии
n! = n *(n – 1)! → как функция F(n) = n *f(n – 1) – задача проще, чем исходная

    int64_t factorial(int16_t n) // потребляет число
    {
        cout << "factorial(" << n << ") is called. \n";
        int64_t result;
        if (n == 0) {  // базовый случай(крайний)
            result = 1;
        } else {       // рекурсивный случай (можно без else)
            result = factorial(n — 1)*n; // можно return вместо result
        }
        cout << "factorial(" << n << ") is exitting.\n";
        return result;}
    
    int main(){
        int16_t x;
        std::cin >> x;
        std::cout << factorial(x) << '\n';}
    
синхронный вызов — ф спит в тот момент, когда выполн др.
когда вызывается ф из ф-ии, то первая ф не перестает существовать и выполняться(все ее лок пер продолжают жить, под них хранится Оперативка). Перед тем как писать рекурсию, н\подумать на бумаге.
Алгоритм эвклида, поиск наибольшего общего делителя.

    int gcd(int a, int b)  {    return (b == 0) ? a : gcd(b, a % b);}
    int main()
    {    int a, b;
    cin >> a >> b;
    cout << gcd(a, b) << '\n';}

ханнойские башни (увидели рекурсию с двойным ветвлением(сказано к слову))

    void hanoi(int i, int k, int n){ // void — распечатываем решение // I стартовый, k финишный, n номер диска
        if (n == 1) { // крайний случай, ничего делать не нужно, ничего кроме распечатки перекладываемого блина, с I на k столбец                   cout << "Move disk 1 from pin " << i   << " to pin " << k << ".\n";
        } else { // рекурентный случай(больше 1го блина)
            int tmp = 6 - i - k; // third pin (temporary)
            hanoi(i, tmp, n — 1); // вызываем друга, и говорим — переложи с I столбца на временный
            cout << "Move disk " << n << " from pin " << i     << " to pin " << k << ".\n";
            hanoi(tmp, k, n — 1); // перекладываем с временного на k
        }   }  int main(){
        hanoi(1, 2, 4); }

Комбiнаторные объекты — генерация

    const int MAX_BINARY_DIGITS_TO_GENERATE = 100;
    // digits_left_to_generate — колво цифр оставшихся к генерации
    void generate_binary_numbers(int digits_left_to_generate){ // распечатывает в крайнем случае
        static int digits_combination[MAX_BINARY_DIGITS_TO_GENERATE]; // чтобы помнить все предварительные предположения, храним в стат Мсе, м\сделать его внутри Фии — лок стат Мс
        static int top = 0; // уровень заполнения(к выводу)
    
        if (digits_left_to_generate == 0) {  // крайний случай(базовый), когда длина для распечатки = 0, т. е. Сгенер полную длину
            for(int i = 0; i < top; i++) // печатаем
                std::cout << digits_combination[i]; // печатаем сгенер число
            std::cout << '\n'; 
        } else {  // рекурентный случай
            digits_combination[top++] = 1; // в правой кладем 1,  в левой 0
            generate_binary_numbers(digits_left_to_generate - 1);
            top--;
    
            digits_combination[top++] = 0;// предположим, и положим от топовой позиции 0
            generate_binary_numbers(digits_left_to_generate - 1);
            top--;
        }
    }
    int main() {    int n;        std::cin >> n;
        generate_binary_numbers(n); } // не полностью корректная ситуация, говорим, какой длины н\сделать

Не н\ перебирать ВСЕ варианты, можно сократить до Нужных

### 10

Перебор с возвратом (метод ветвей и границ)
Полный перебор — всегда долго
генерация перестановок

    const int MAX_BINARY_DIGITS_TO_GENERATE = 100;
    
    void permutations(int16_t number, int16_t current, int16_t buffer[], bool used[]) { //1кол-во 2 Мс из чисел 3 текущее  4 Мс флагов(bool) дб размера namber
        if (current == number) {  // крайний\базовый случай
            for(int i = 0; i < number; i++)
                std::cout << buffer[i] << ' ' << '\n';  // печатаем в крайнем случае - буфер
        } else {  // рекурсивный случай
            for (int16_t variant = 0; variant < number; variant++) { // этот рекурентный вызов  permutations делать с выстановкой в буфере в н\ой позиции в тек позиции этого самого  варианта, делаем на каждой итерации цикла
                if (not used[variant]) { // (подрезание рекурсивного дерева) отсечение границ(used именно для этого) used – bool и не н\писать == true, н\если не использовали, будем исп 
                    buffer[current] = variant;
                    used[variant] = true; // перед тем как поставить в буфер/одновременно, отметим что этот вариант исп-ся, чтобы более глубокие уровни рекурсии доступаясь к тому же самому им Мсу used, увидели что вариант уже исп-ван. Когда пойдем на др ветви, н\отменить факт исп-ия
                    permutations(number, current + 1, buffer, used); // глобальная задача, запустить  permutations

вложенная задача, рекурентно запущенная д\генер все перестановки начиная со след цифры current + 1, но буфер передаем как есть, но естесно buffer в позиции [current] положить в  = variant, всевозможные варианты, начиная от 0 до number не включительно(делаем циклом)

                    used[variant] = false;
                }
            }
        }
    }
    int main() {
        int16_t n;     std::cin >> n;
        if (n > 20) {  return 1;  // большой рост перестановок 20!
            
        } else if (n <= 0) {  return 1;    }
    
        int16_t buffer[n]; // вводим
        bool used[n] = {false}; // предполагаем что used будет инициализирован нулями (интерпритироваться как false)
        permutations(n, 0, buffer, used); // передаем 1 колво, 2 тек позиция 3 буфер
    } 
//Лишние контракты вредят, лучше бы, чтобы и буфер и used создавался внутри ф-ии с точки зрения интерфейса взаимодействия с конечным пользователем вызывающим  permutations(n, 0, buffer, used) это создает излишние проблемы  для последующего исп-ия фии генерации перестановок

Статические переменные плохи(глобальные которые Не конст, на такие пер нужно создавать мьютексы), потому что мб параллельные вычисления, и один поток уже взял, но не вернул, а другой хочет взять, но не обнаруживает.(а пер то всего одна)

Быстрые рекурентные сортировки
1 тони хора
2 слиянием
Рекурсивная быстрая сортировка слиянием

    const int MAX_ARRAY_SIZE = 100000;
    
    void merge_sort(double *array, int16_t array_size){
        if (array_size <= 1) return;  // крайний(базовый) случай, критически важно(иначе в бесконечность)   
        int16_t middle = array_size / 2; // определяем середину
        double *left = array; // адреса старта
        double *right = array + middle;  // адреса старта
        int16_t left_size = middle; 
        int16_t right_size = array_size — left_size; // внимание, адресная арифметика pointer + number дает сдвиг начала Мса
        
        merge_sort(left, left_size); // рекурсия начинается здесь \ разделяй и властвуй
        merge_sort(right, right_size);
        // м\ли left и right сортировать и складывать внутрь array – нет. М\оказаться что перезаписываем left прямо в процессе(правые элы оказываются меньше левых и записываем их поверх левых, array_left указатель на одну и туже память. Значит ВП внутри которой будем осуществлять слияние, а потом скопировать обратно
        // Merge здесь 2 готорые к сортировке половины
        double *buffer = new double[array_size]; // назовем его буфер
        int16_t left_i = 0; // делаем слияние left и right в буфер, понадобится 3 пер
        int16_t right_i = 0; // правы текущий
        int16_t buffer_i = 0; // текущий в буфере
        while (left_i < left_size and right_i < right_size) { // пока хотя бы одна из половинок не закончилась, 
            if (left[left_i] <= right[right_i]) { // продолжаем сравнивать того, кто лежит в левой половинке  по индексу [left_i](это текущий эл из левой половинки), если <= берем его.(берем меньшего из левой половины Мса)
                buffer[buffer_i] = left[left_i]; // в буфер, в позицию [buffer_i] кладем левый эл, который сравнивали
                left_i += 1; // сдвиг left_i
                buffer_i += 1; // сдвиг buffer_i
            } else { // (берем меньшего из левой половины Мса)
                buffer[buffer_i] = right[right_i]; // почти копия
                right_i += 1;
                buffer_i += 1;
            }
        }
        while (left_i < left_size) { // копируем оставшиеся элы из  left size (if there is right something)
            buffer[buffer_i] = left[left_i];
            left_i += 1;
            buffer_i += 1;
        }
        while (right_i < right_size) { // почти копия
            buffer[buffer_i] = right[right_i];
            right_i += 1;
            buffer_i += 1;
        }    
        // copying from buffer to original array:
        for(int16_t i = 0; i < array_size; i++) { // копируем из буфера в оригинальный Мс
            array[i] = buffer[i];
        }
        delete[] buffer;
    }
    void input_array(double *array, int16_t n){
        for (int i = 0; i < n; i++) {
            std::cin >> array[i]; // надеемся что ВП, иначе это вина того, кто вызвал эту Фю
        }
    }
    void print_array(double *array, int16_t n){
        for (int i = 0; i < n; i++) {
            std::cout << array[i] << ' ';
        } 
    }
    
    int main(){
        int16_t array_size;
        cin >> array_size; // вводим размер Мса
        if (array_size <= 0 or array_size > MAX_ARRAY_SIZE) { // н\ограничить размер (не запредельный\отриц)
            return 1; }
        double *array = new double[array_size]; // двп размера Мса
        
        input_array(array, array_size); // вводим Мс
        merge_sort(array, array_size); // идеально передать просто Мс, но если это не «готовый вектор»\ контейнером, н\указать еще и размер
        print_array(array, array_size);
        delete[] array;}

### 11

Динамическое программирование
числа фибоначчи

    uint64_t fib_recursive(int n){
        assert(n >= 0);
        if (n == 0 or n == 1) { //крайний случай
            return n;
        } else {
            return fib_recursive(n-1) + fib_recursive(n-2); // если рекурентный случай
        }
    }
    uint64_t fib_dynamic(int n){
        uint64_t result;
        uint64_t *fib = new uint64_t[n + 1]; // n + 1 элов
        fib[0] = 0; // крайний случай
        fib[1] = 1;
        for (int i = 2; i <= n; i++) {
            fib[i] = fib[i-1] + fib[i-2]; // очередное, опираясь на предыдущее(важно не получать не вычисленные знач)
        }   
        result = fib[n];
        delete[] fib;
        return result;
    }
    int main(){
        uint64_t (*fib)(int); // указатель на фю, 
        int version = 0;  std::cin >> version;
        if (version == 0) {        fib = fib_recursive;
        } else {        fib = fib_dynamic;    }
        for (int n = 0; n <= 100; n++) {
            std::cout << n << '\t' << fib(n) << '\n';
        }  }

### Задача о кузнечике

    
    int min_cost(int n, int price[]){
        int cost[n + 1]; // делаем на стеке
        cost[1] = price[1];  // крайний случай
        cost[2] = price[1] + price[2]; // крайний случай
        for (int i = 3; i <= n; i++) {
            cost[i] = std::min(cost[i-1], cost[i-2]) + price[i];  }   // рекурсивный случай, минимум из 1 и 2 и добавляем  price[i], т. к. в эту клетку полюбому н\наступить
        int current = n; // начнем с клетки n (для печати)
        cout << current << " "; //дополнительно до цикла 1й 
        while(current != 1) { // вывод, показывающий выбор клеток кроликом
            if (cost[current - 1] == cost[current] - price[current])
                current = current - 1;
            else if (cost[current - 2] == cost[current] - price[current])
                current = current - 2;
            else            throw -1;  }// Такого не\м\б
       cout << current; // остальные
        return cost[n]; // результат
    }
    int main(){
        int n;    std::cin >> n;
        if (n > 100) {        return -1;    }
        int price[101];        std::cout << "Enter prices \n";
        for (int i = 1; i <= n; i++) {        std::cin >> price[i];    }
        std::cout << min_cost(n, price) << '\n';
    }

### 12

двумарное динамо программирование
В матрицах указывается сначала НОМЕР строки I, а потом указывается номер ЭЛЕМЕНТА в строке.
MxN = 1280x720, а координаы назваем наоборот 1280 j, 720 I
когда делаем динамику, в отличие от рекурсии, очень важно отслеживать траекторию вычислений. Вычисляем новое значение ТОЛЬКО по старым, не по еще Не вычиленным.
Есть Ф и есть ее область определения фии, аглгоритм д\ее вычислить и ответить чему же эта ф равна. При этом, для каких-то ситуаций знаем знач Фии\м\пряво посчитать. Это крайний случай. Остальные Не знаем, но умеем сводить эти случаи к крайнему. В рекурсии берем требуемый случай(значение), рекурсия уменьшает сложность задачи сводя ее к другой задаче(более легкой). Решив задачу, возвращаемся назад. Итого — поиск траектории вычислений у рекурсии находится на собственном попечении, а у динама Прния это наша задача, рассчитывать значения, расширять знания о фии, так чтобы в какой-то момент добраться до нужного случая, и в этот момент м\останавливаться.
Муравей\ переделали фибоначи
задача комбинаторики колво способов из 5 выбрать 2 дежурных = с из н по к(треугольник паскаля)

    uint64_t combinations_recursive(int i, int j){ // рекурсия
        assert(i > 0 and j > 0); // делаем разумные вещи
        if (i == 1 or j == 1) {       return 1; // значит колво траекторий = 1
        } else {        return combinations_recursive(i, j-1) + combinations_recursive(i-1, j);    }
    }
    uint64_t combinations_dynamic(int n, int m){
        uint64_t result;
        uint64_t **K = new uint64_t*[n + 1];  // К указатель на указатьль динамо указатель инт
    memory allocation for K function:
        for(int i = 0; i <= n; i++) { // ДВП циклом
            K[i] = new uint64_t[m + 1];
        }
        for (int i = 1; i <= n; i++) {  // крайний случай(циклом, все единицы)
            K[i][1] = 1; } важно что слева на право и сверху вниз
        for (int j = 1; j <= m; j++) {
            K[1][j] = 1;  }
       
        for (int i = 2; i <= n; i++) { // рекурентный случай(вычисляем динамо)
            for (int j = 2; j <= m; j++) {
                K[i][j] = K[i-1][j] + K[i][j-1];
            }
        }
        // return value with correct liberation of allocated memory
        result = K[n][m]; // ради одного числа(вроде н)
        for(int i = 0; i <= n; i++) // освобождаем память циклом
            delete K[i];
        delete[] K;
        return result;
    }
    int main(){
        uint64_t (*combinations)(int, int); // указатель на фю
        int version = 0;
        std::cout << "Which version of function to use? (0 - recursive, 1 - dynamic)\n";
        std::cin >> version;
        if (version == 0) {        combinations = combinations_recursive;
        } else {        combinations = combinations_dynamic;    }
        for (int i = 1; i <= 30; i++) { // выводим всю таблицу
            for (int j = 1; j <= 12; j++) {
                std::cout << combinations(i, j) << '\t';       }        std::cout << '\n';
        }
    }

векторы — динамически расширяемый Мс для любого типа(шаблонный класс, с вложенными в него шаблонными классами итераторов)
— когда A[i] == *(A + I) — вектор как и Мс — структура произвольного доступа

    vector<int> A; // одномерный вектор
    
    array версия муравья (почти копия)
    uint64_t combinations_recursive(int i, int j){
        assert(i > 0 and j > 0);
        if (i == 1 or j == 1) {        return 1;
        } else {        return combinations_recursive(i, j-1) + combinations_recursive(i-1, j);
        }}
    uint64_t combinations_dynamic(int n, int m){
        std::vector<std::vector<uint64_t>> K;
        K.resize(n + 1); // первый раз ВП
        for (int i = 1; i <= n; i++) { K[i].resize(m + 1); } // второй раз ВП
        for (int i = 1; i <= n; i++) { K[i][1] = 1; } // base cases:
        for (int j = 1; j <= m; j++) { K[1][j] = 1; }   
        for (int i = 2; i <= n; i++) {  // recursive cases:
            for (int j = 2; j <= m; j++) {
                K[i][j] = K[i-1][j] + K[i][j-1];        }    }   
        return K[n][m];
    }
    int main(){   }
    Задача об укладке рюкзака
    double max_backpack_value(std::vector<std::pair<int, double>> treasures, int capacity){
        std::vector<std::vector<double>> F;// 2D Мс ответов сюда будут заполняться
        F.resize(capacity + 1); //  capacity включительно(строки)
        for (int i = 0; i <= capacity; i++) { F[i].resize(treasures.size() + 1); }    std::cout << "DEBUG 1\n"; 
        for (int i = 0; i <= capacity; i++) {        F[i][0] = 0;    } // крайний случай
        for (int j = 0; j <= treasures.size(); j++) {        F[0][j] = 0;    }   std::cout << "DEBUG 2\n";

    for (int j = 1; j <= treasures.size(); j++) {// рекурентный случай
        int weight = treasures[j-1].first;
        double value = treasures[j-1].second;
    
            for (int k = 1; k < weight; k++) {            F[k][j] = F[k][j-1];        }
            for (int k = weight; k <= capacity; k++) { F[k][j] = std::max(F[k][j-1], value + F[k-weight][j-1]);  }  
      }   
        return F[capacity][treasures.size()];
    }
    int main(){
        int treasures_number;    std::cin >> treasures_number;
        std::vector<std::pair<int, double>> treasures; // сами сокровища(пары информации)
        for (int i = 0; i < treasures_number; i++) {
            int weight; // вес
            double value; // ценность
            std::cout << "Enter treasure[" << i << "] weight and value:";
            std::cin >> weight >> value;
            treasures.push_back(std::make_pair(weight, value)); // отправляем в нужный I эл с пом .push_back, std::make_pair из  weight, value
        }
        int capacity;   std::cin >> capacity;
        std::cout << max_backpack_value(treasures, capacity) << '\n';}
    

### 13 пропустил там char 

### 14
Контейнеры и строки
