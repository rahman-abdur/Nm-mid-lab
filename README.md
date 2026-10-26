# Nm-mid-lab
Nm

Horners Rule:
#include <iostream>
using namespace std;

int main()
{
    int a[100], n, x, i;
    long long result;

    cin >> n;

    // Check degree
    if(n < 0 || n > 99)
    {
        cout << "Invalid degree";
        return 0;
    }

    for(i = 0; i <= n; i++)
        cin >> a[i];

    cin >> x;

    result = a[0];

    for(i = 1; i <= n; i++)
        result = result * x + a[i];

    cout << "Result = " << result;

    return 0;
}
Bisection:


#include <iostream>
#include <cmath>
using namespace std;

double f(double x)
{
    return x*x*x - x - 2;
}

int main()
{
    double a, b, c, e;

    cin >> a >> b >> e;  // User input

    // Check tolerance
    if (e <= 0)
    {
        cout << "Invalid tolerance";
        return 0;
    }

    // Check interval
    if (f(a) * f(b) >= 0)
    {
        cout << "Invalid interval";
        return 0;
    }

    while (true)
    {
        c = (a + b) / 2;

        if (fabs(f(c)) < e)
            break;

        if (f(a) * f(c) < 0)
            b = c;
        else
            a = c;
    }

    cout << "Root = " << c;

    return 0;
}
Newton forward Interpolation:


#include <iostream>
using namespace std;

int main()
{
    int n;
    double x[10], y[10][10], value, h, u, result, p;

    cin >> n;

    for (int i = 0; i < n; i++)
        cin >> x[i] >> y[i][0];

    cin >> value;

    h = x[1] - x[0];
    u = (value - x[0]) / h;

    for (int j = 1; j < n; j++)
    {
        for (int i = 0; i < n - j; i++)
            y[i][j] = y[i + 1][j - 1] - y[i][j - 1];
    }

    result = y[0][0];
    p = 1;

    for (int i = 1; i < n; i++)
    {
        p = p * (u - i + 1) / i;
        result = result + p * y[0][i];
    }

    cout << "Result = " << result;

    return 0;
}
Newton divided interpolation:


#include <iostream>
using namespace std;

int main()
{
    int n;
    double x[10], y[10][10], value, result, p;

    cin >> n;

    for (int i = 0; i < n; i++)
        cin >> x[i] >> y[i][0];

    cin >> value;

    for (int j = 1; j < n; j++)
    {
        for (int i = 0; i < n - j; i++)
            y[i][j] = (y[i + 1][j - 1] - y[i][j - 1])
                    / (x[i + j] - x[i]);
    }

    result = y[0][0];
    p = 1;

    for (int i = 1; i < n; i++)
    {
        p = p * (value - x[i - 1]);
        result = result + p * y[0][i];
    }

    cout << "Result = " << result;

    return 0;
}
Bankers:


#include <iostream>
using namespace std;

int main()
{
    double num, factor = 1;
    int n, digit, last;
    long long x;

    cin >> num >> n;

    while (num >= 10)
    {
        num /= 10;
        factor *= 10;
    }

    while (num < 1 && num > 0)
    {
        num *= 10;
        factor /= 10;
    }

    for (int i = 1; i < n; i++)
        num *= 10;

    x = (long long)num;
    digit = (int)(num * 10) % 10;
    last = x % 10;

    if (digit > 5 || (digit == 5 && last % 2 != 0))
        x++;

    cout << x / factor;

    return 0;
}

