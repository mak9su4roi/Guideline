mkdir b_1 && cd b_1
cmake ../search_dir && cmake --build . 		#Create library
cd .. && rm -rf b_1
