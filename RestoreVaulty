#include <iostream>
#include <dirent.h>
#include <istream>
#include <ostream>
#include <fstream>
#include <vector>
#include <string>
#include <algorithm>

using namespace std;

vector<string> open(string path)
{ 
    DIR    *dir; 
    dirent *pdir; 
    vector<string> files; 
    dir = opendir(path.c_str()); 
    while (pdir = readdir(dir)) 
    { 
        files.push_back(pdir->d_name); 
    } 
    return files; 
}  

int main(int argc, char** argv) {
	long size;
	
	string path = "C:/Users/andre/Downloads/Vaulty/";
	
	vector<string> file;
	file = open(path);
	
	for (int i=3; i<file.size(); i++){
		char* memblock;
		string input_path_complete = path + file[i];
		string input_path = input_path_complete;
		input_path.erase(input_path.end()-6, input_path.end());
		string output_path = input_path + ".jpeg";
		ifstream input_file (input_path_complete.c_str(), ios::binary | ios::ate);
		ofstream output_file (output_path.c_str(), ios::binary);
		char* buffer = new char (input_file.tellg());
		size = input_file.tellg();
		memblock = new char [size];
		input_file.seekg (8, ios::beg);
		input_file.read(memblock, size);
		
		output_file.write(memblock, size);
		
		delete[] memblock;
		input_file.close();
		output_file.close();
	}
}
