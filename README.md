//Вариант 6.	Отсортировать слова в алфавитном порядке.
#include <iostream>
#include <cstring>

using namespace std;

struct s
{
    char * word;
};

int main()
{
    char str[] = {"she is beautiful in this attire."};

    int count = 1;
    for (size_t i = 0; str[i] != '\0'; ++i)
    {
        if (str[i] == ' ' && str[i + 1] != ' ') // слово будет считать только, если между словами один пробел и не более
        {
            count++;
        }
    }

    const int N = count;
    s words[N];
    const char *delims = " ,.!?@#$%^&*();:\"\n\t";
    char *token = strtok(str, delims);
    unsigned int i = 0;
    while (token)
    {
        words[i].word = token;
        token = strtok(NULL, delims); 
        i++;
    }
    
    for (size_t i = 0; i < N; ++i)
    {
        for(int j = i+1; j < N; j++)
            if(strcmp(words[i].word, words[j].word) > 0)
            {
                char* tmp = words[i].word;
                words[i].word = words[j].word;
                words[j].word = tmp;
            }
    }
    cout << endl << endl;
    
    for (size_t i = 0; i < N; ++i)
    {
        cout << words[i].word << " ";
    }
    cout << endl << endl;
}
