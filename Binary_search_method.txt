//A program to perform Binary search using iteration and recursion concepts..
#include <iostream>
using namespace std;

class Binary_search
{
    int size; //Data members.
    int value, high, low, mid;
    int arr[];

public:
    //constructor that initializes 0 to variable low.
    Binary_search(void)
    {
        low = 0;
    }
    void getArray(int n) //A public function to input the array from user.
    {
        size = n;
        cout << "Enter the array [" << n << "] :\n";
        for (int i = 0; i < size; i++)
        {
            cin >> arr[i];
        }
        high = size - 1;
    }
    void displayArray(void) //A public function to display the array.
    {
        cout << "\nArray is :" << endl;
        for (int i = 0; i < size; i++)
        {
            cout << arr[i] << " ";
        }
        cout << endl;
    }
    void result(int inp) //A public function to display result of search.
    {
        if (inp == -1)
        {
            cout << "Element not Found !! " << endl;
        }
        else
            cout << "Element found at index " << inp << endl;
    }

    int iterativebin_search(int); //A public function to search any element from the input array using iterative method.
    int recursivebin_search(int); //A public function to search any element from the input array using recursive method.
};
typedef Binary_search bsc; // rename Binary_search class to bsc.

int bsc ::iterativebin_search(int element)
{
    value = element;
    high = size - 1;
    while (low <= high)
    {
        mid = (high + low) / 2;
        if (element == arr[mid])
            return mid;

        if (element > arr[mid])
            low = mid + 1;

        else
            high = mid - 1;
    }
    return -1;
}
int bsc ::recursivebin_search(int element)
{
    value = element;
    if (low <= high)
    {
        mid = (high + low) / 2;
        if (element == arr[mid])
            return mid;

        if (element > arr[mid])
        {
            low = mid + 1;
            return recursivebin_search(element);
        }

        else
        {
            high = mid - 1;
            return recursivebin_search(element);
        }
    }
    return -1;
}

int main(void)
{
    bsc b1;
    int search_element;
    b1.getArray(5);
    b1.displayArray();
    cout << "Enter the element you want to search >> ";
    cin >> search_element;
    b1.result(b1.recursivebin_search(search_element));

    return 0;
}