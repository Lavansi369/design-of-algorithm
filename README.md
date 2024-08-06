
#include <conio.h>
#include <graphics.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <direct.h> //contains functions for manipulating system directories

/* A Naive recursive implementation
of 0-1 Knapsack problem */

// A utility function that returns
// maximum of two integers
int max(int a, int b) { return (a > b) ? a : b; }

// Returns the maximum value that can be
// put in a knapsack of capacity W
int knapSack(int W, int wt[], int val[], int n)
{
	// Base Case
	if (n == 0 || W == 0)
		return 0;

	// If weight of the nth item is more than
	// Knapsack capacity W, then this item cannot
	// be included in the optimal solution
	if (wt[n - 1] > W)
		return knapSack(W, wt, val, n - 1);

	// Return the maximum of two cases:
	// (1) nth item included
	// (2) not included
	else

		return max(
			val[n - 1] + knapSack(W - wt[n - 1], wt, val, n - 1),
			knapSack(W, wt, val, n - 1));
}

// Driver code

void outline()
{
	int u = 400;

	// Storing Box Outline
	rectangle(700, 300, 1000, 900);

	// Vertical Lines To Make
	// Divisions
	line(800, 300, 800, 900);
	line(900, 300, 900, 900);

	// Making Horizontal Line Using
	// While Function
	while (u <= 900)
	{
		line(700, u, 1000, u);
		u = u + 100;
	}

	// Printing The Instruction
	// On Screen
	settextstyle(10, 0, 3);								   // function used to chage the way the text appears
	outtextxy(20, 100, (char *)"FOR MOVE LEFT PRESS 'l'"); // display text at current position
	outtextxy(20, 200, (char *)"FOR MOVE RIGHT PRESS 'r'");
	outtextxy(20, 300, (char *)"FOR MOVE MIDDLE PRESS 'm'");
}

// Driver Code
int main()

{

	int profit[] = {60, 100, 120};
	int weight[] = {10, 20, 30};
	int W = 50;
	outline();
	int n = sizeof(profit) / sizeof(profit[0]);
	printf("%d", knapSack(W, weight, profit, n));

	return 0;
	// The first parameter (gd) is a pointer to the graphics driver, which is set to DETECT
	// to detect the graphics driver automatically.

	int gd = DETECT, gm;
	int height = GetSystemMetrics(SM_CYSCREEN);
	int width = GetSystemMetrics(SM_CXSCREEN);
	initwindow(width, height, "windows bgi", -5, -5);

	// Initialize of gdriver with
	// DETECT macros
	// initgraph(&gd, &gm, (char *)"");

	// Declaring & Initialising Variables
	int a = 800, b = 50, c = 900, d = 150,
		x, left[10], right[10], mid[10],
		up = 5, low = 2, lb = 900, mb = 900,
		rb = 900, i = 0, j = 0, k = 0,
		score = 0, p;
	char z, str[3];

	// Calling outline() function
	outline();

	// Creating Infinite Loop To Make
	// Continuous Use OF Game
	while (1)
	{
		// Creating & Naming The
		// Brick Box
		settextstyle(8, 0, 2);
		outtextxy(800, 10, (char *)"Brick Box");
		rectangle(a, b, c, d);

		// Generating Random Color Number
		x = (rand() % (up - low + 1)) + low;
		setfillstyle(SOLID_FILL, x);
		floodfill(a + 5, d - 5, 15);

		// Getting Input To Move Bricks
		z = getch();

		// Operations For Place The Bricks
		// In Left Side
		if (z == 'l')
		{
			// Creating & Naming The Left
			// Sub-Box
			settextstyle(8, 0, 2);
			outtextxy(630, 10, (char *)"Left Sub-Box");

			rectangle(a - 150, b, c - 150, d);
			floodfill(a - 55, d - 5, 15);
			delay(200);
			setfillstyle(SOLID_FILL, BLACK);
			floodfill(a - 55, d - 5, 15);
			rectangle(a - 100, lb - 100,
					  c - 100, lb);
			setfillstyle(SOLID_FILL, x);
			floodfill(a - 5, lb - 5, 15);
			delay(200);

			// Decreasing The Base Of
			// Left Side
			lb = lb - 100;

			// Storing Corresponding Color
			// In Left[] Array
			left[i] = x;
			i++;

			// Process To Check Is There Any
			// Matching In The Left Side By
			// Upside Down
			if (left[0] == left[1])
			{
				lb = 900;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a - 5, lb - 5, 15);
				floodfill(a - 5, lb - 105, 15);
				score = score + 10;
				i = 0;
				left[1] = 0;
			}
			else if (left[1] == left[2])
			{
				lb = 800;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a - 5, lb - 5, 15);
				floodfill(a - 5, lb - 105, 15);
				score = score + 10;
				i = 1;
				left[2] = 0;
			}
			else if (left[2] == left[3])
			{
				lb = 700;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a - 5, lb - 5, 15);
				floodfill(a - 5, lb - 105, 15);
				score = score + 10;
				i = 2;
				left[3] = 0;
			}
			else if (left[3] == left[4])
			{
				lb = 600;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a - 5, lb - 5, 15);
				floodfill(a - 5, lb - 105, 15);
				score = score + 10;
				i = 3;
				left[4] = 0;
			}
			else if (left[4] == left[5])
			{
				lb = 500;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a - 5, lb - 5, 15);
				floodfill(a - 5, lb - 105, 15);
				score = score + 10;
				i = 4;
				left[5] = 0;
			}
			else
				p = 0;

			// Loop Breaking Condition For
			// Left Side
			if (lb < 400)
				break;
		}

		// Operations For Place The Bricks
		// In Right Side
		else if (z == 'r')
		{
			// Creating & Naming The Left
			// Sub-Box
			settextstyle(8, 0, 2);
			outtextxy(970, 10, (char *)"Right Sub-Box");

			rectangle(a + 150, b, c + 150, d);
			floodfill(a + 155, d - 5, 15);
			delay(200);
			setfillstyle(SOLID_FILL, BLACK);
			floodfill(a + 155, d - 5, 15);
			rectangle(a + 100, rb - 100,
					  c + 100, rb);
			setfillstyle(SOLID_FILL, x);
			floodfill(a + 105, rb - 5, 15);
			delay(200);

			// Decreasing The Base Of
			// Right Side
			rb = rb - 100;

			// Storing Corresponding Color
			// In Right[] Array
			right[j] = x;
			j++;

			// Process to Check Is There Any Matching
			// In The Right Side By Upside Down
			if (right[0] == right[1])
			{
				rb = 900;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 105, rb - 5, 15);
				floodfill(a + 105, rb - 105, 15);
				score = score + 10;
				j = 0;
				right[1] = 0;
			}
			else if (right[1] == right[2])
			{
				rb = 800;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 105, rb - 5, 15);
				floodfill(a + 105, rb - 105, 15);
				score = score + 10;
				j = 1;
				right[2] = 0;
			}
			else if (right[2] == right[3])
			{
				rb = 700;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 105, rb - 5, 15);
				floodfill(a + 105, rb - 105, 15);
				score = score + 10;
				j = 2;
				right[3] = 0;
			}
			else if (right[3] == right[4])
			{
				rb = 600;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 105, rb - 5, 15);
				floodfill(a + 105, rb - 105, 15);
				score = score + 10;
				j = 3;
				right[4] = 0;
			}
			else if (right[4] == right[5])
			{
				rb = 500;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 105, rb - 5, 15);
				floodfill(a + 105, rb - 105, 15);
				score = score + 10;
				j = 4;
				right[5] = 0;
			}
			else
				p = 0;

			// Loop Breaking Condition For
			// Right Side
			if (rb - 100 < 300)
				break;
		}

		// Operations For Place The Bricks
		// In Middle Side
		else
		{
			rectangle(a, mb - 100, c, mb);
			floodfill(a + 5, mb - 5, 15);
			delay(200);

			// Decreasing The Base Of
			// Middle Side
			mb = mb - 100;

			// Storing Corresponding Color In
			// Mid[] Array
			mid[k] = x;
			k++;

			// Process To Check Is There Any
			// Matching In The Middle Side
			// By Upside Down
			if (mid[0] == mid[1])
			{
				mb = 900;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 5, mb - 5, 15);
				floodfill(a + 5, mb - 105, 15);
				score = score + 10;
				k = 0;
				mid[1] = 0;
			}
			else if (mid[1] == mid[2])
			{
				mb = 800;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 5, mb - 5, 15);
				floodfill(a + 5, mb - 105, 15);
				score = score + 10;
				k = 1;
				mid[2] = 0;
			}
			else if (mid[2] == mid[3])
			{
				mb = 700;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 5, mb - 5, 15);
				floodfill(a + 5, mb - 105, 15);
				score = score + 10;
				k = 2;
				mid[3] = 0;
			}
			else if (mid[3] == mid[4])
			{
				mb = 600;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 5, mb - 5, 15);
				floodfill(a + 5, mb - 105, 15);
				score = score + 10;
				k = 3;
				mid[4] = 0;
			}
			else if (mid[4] == mid[5])
			{
				mb = 500;
				setfillstyle(SOLID_FILL, BLACK);
				floodfill(a + 5, mb - 5, 15);
				floodfill(a + 5, mb - 105, 15);
				score = score + 10;
				k = 4;
				mid[5] = 0;
			}
			else
				p = 0;

			// Loop Breaking Condition For
			// Middle Side
			if (mb - 100 < 300)
				break;
		}

		// Time Delay
		delay(200);

		// Display Score Whenever There Is.graph1

		// Any Match
		sprintf(str, "%d", score);
		outtextxy(100, 600, (char *)"SCORE: ");
		outtextxy(100, 700, str);
	}

	// Time Delay
	delay(500);

	// Clearing The Screen When Game
	// Is Over
	cleardevice();

	// Holding screen for a while
	getch();

	// Close the initialized gdriver
	closegraph();
}
