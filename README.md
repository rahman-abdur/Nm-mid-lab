#include<stdio.h>
#include<conio.h>
#include<graphics.h>

int main()
{
    int gd=DETECT,gm;
    int xc,yc,r;
    int x,y,d;

    printf("Enter center (xc,yc): ");
    scanf("%d%d",&xc,&yc);

    printf("Enter radius: ");
    scanf("%d",&r);

    initgraph(&gd,&gm,"C:\\TurboC3\\BGI");

    x=0;
    y=r;
    d=3-2*r;

    while(x<=y)
    {
        putpixel(xc+x,yc+y,WHITE);
        putpixel(xc-x,yc+y,WHITE);
        putpixel(xc+x,yc-y,WHITE);
        putpixel(xc-x,yc-y,WHITE);
        putpixel(xc+y,yc+x,WHITE);
        putpixel(xc-y,yc+x,WHITE);
        putpixel(xc+y,yc-x,WHITE);
        putpixel(xc-y,yc-x,WHITE);

        if(d<0)
            d=d+4*x+6;
        else
        {
            d=d+4*(x-y)+10;
            y--;
        }

        x++;
    }

    getch();
    closegraph();
    return 0;
}
