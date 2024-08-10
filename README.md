#include <iostream>
#include <cmath>
//this is only being use dfor doing power half for all  others i have created my own power function
using namespace std;
int fact(int i)
{
    int j = 1;
    for (int k = 1; k <= i; k++)
    {
        j = j * k;
    }
    return (j);
}
double power(double i, double j)
{
    int k;
    double answer = 1;
    for (k = 1; k <= j; k++)
    {
        answer = answer * i;
    }
    return (answer);
}
float sinefxn(float x)
{
    float pi = 3.141592;
    float answer = 0;
    x = x * (pi / 180);
    for (int i = 0; i <= 15; i++)
    {
        answer = answer + power(-1, i) * (power(x, 2 * i + 1) / fact(2 * i + 1));
    }
    return (answer);
}
float cosfxn(float x)
{
    float answer = 0;
    float pi = 3.141592;
    x = x * pi / 180;
    for (int i = 0; i <= 15; i++)
    {
        answer = answer + power(-1, i) * (power(x, 2 * i) / fact(2 * i));
    }
    return (answer);
}

int main()
{
    float num1, num2;
    int num11, num22;
    char ope;
    cout << "welcome\n";
    int option;
    cout << "you have the following options\n1)add sub mul div modulo\n2)power\n3)quadratic expression solving\n4)trigonometric fuctions\n5)logarithm functions\n";
    cout<<"enter in your option number/n;
    std::cin >> option;
    switch (option)
    {
    case (1):
    {
        cout << "enter the question in the format of num ope num\n";
        std::cin >> num1 >> ope >> num2;

        if (ope == '+')
        {
            cout << "answer=" << num1 + num2 << endl;
        }
        if (ope == '-')
        {
            cout << "answer=" << num1 - num2 << endl;
        }
        if (ope == '*')
        {
            cout << "answer=" << num1 * num2 << endl;
        }
        if (ope == '/')
        {
            cout << "answer=" << num1 / num2 << endl;
        }
        if (ope == '%')
        {
            num11 = num1;
            num22 = num2;
            cout << "answer=" << num11 % num22 << endl;
        }
        break;
    }
    case (2):
    {
        double pownum1, pownum2;
        cout << "enter the numbers" << endl;
        std::cin >> pownum1 >> pownum2;
        cout << "the answer is " << power(pownum1, pownum2) << endl;
        break;
    }
    case (3):
    {
        float a, b, c;
        cout << "please enter the values of coefficient of x^2,x,const in the same order\n";
        std::cin >> a >> b >> c;
        double answer1, answer2, value;
        value = pow(b, 2) - 4 * a * c;
        if (value >= 0)
        {
            answer1 = ((-b) + pow(value, 0.5))/(2*a);
            answer2 = ((-b) - pow(value, 0.5))/(2*a);
            cout << answer1  << "," << answer2  << endl;
        }
        else if (value < 0)
        {
            double valuemod = value * (-1);
            cout << "your equation has no real roots\n";
            cout << "your roots are something like -" << b /(2*a)<< "+i" << "(" << pow(valuemod, 0.5)/(2*a) << ") and";
            cout << "-" << b/(2*a) << "-i" << "(" << pow(valuemod, 0.5)/(2*a) << ")" << endl;
        }
        break;
    }
    case (4):
    {
        cout << "which trigonometric ratio do you want to find\n1)sin\n2)cos\n3)tan\n4)cot\n5)sec\n6)cosec\n";
        cout << "enter the option number\n";
        int option;
        cin >> option;
        switch (option)
        {
        case (1):
        {
            cout << "please enter the value of angle whose sine value u want to calculate(in degs),make sure the value lies in the principal domain\n";
            float x;
            cin >> x;
            cout << "sin(" << x << ")=" << sinefxn(x) << endl;
            break;
        }
        case (2):
        {
            cout << "please enter the value of angle whose cos value u want to calculate(in degs),make sure the value lies in the principal domain\n";
            float x;
            cin >> x;
            cout << "cos(" << x << ")=" << cosfxn(x) << endl;
            break;
        }
        case (3):
        {
            cout << "please enter the value of angle whose tan value u want to calculate(in degs),make sure the value lies in the principal domain\n";
            float x;
            cin >> x;
            cout << "tan(" << x << ")=" << sinefxn(x) / cosfxn(x) << endl;
            break;
        }
        case (4):
        {
            cout << "please enter the value of angle whose cot value u want to calculate(in degs),make sure the value lies in the principal domain\n";
            float x;
            cin >> x;
            cout << "cot(" << x << ")=" << cosfxn(x) / sinefxn(x) << endl;
            break;
        }
        case (5):
        {
            cout << "please enter the value of angle whose sec value u want to calculate(in degs),make sure the value lies in the principal domain\n";
            float x;
            cin >> x;
            cout << "sec(" << x << ")=" << 1.0 / cosfxn(x) << endl;
            break;
        }
        case (6):
        {
            cout << "please enter the value of angle whose cosec value u want to calculate(in degs),make sure the value lies in the principal domain\n";
            float x;
            cin >> x;
            cout << "cosec(" << x << ")=" << 1.0 / sinefxn(x) << endl;
            break;
        }
        }
        break;
    }
    case (5):
    {
        float num;
        cout << "enter the number whose log u want ot find out\n";
        cin >> num;
        int i = 0;
        while (num / power(2.72, i) > 1)
        {
            i++;
        }
        num = num / power(2.72, i);
        num = num - 1;

        float answer = 0;
        for (int i = 1; i <= 30; i++)
        {
            answer = answer + power(-1, i - 1) * ((power(num, i)) / i);
        }
        answer = answer + i;
        cout << "the answer approximately is " << answer << endl;
        break;
    }
    }
}
