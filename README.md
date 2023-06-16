# import all functions from the tkinter 
from tkinter import *//import library 
# import messagebox class from tkinter 
from tkinter import messagebox //import library

# menghapus konten dari entry box

	dayField.delete(0, END) 
	monthField.delete(0, END) 
	yearField.delete(0, END) 
	givenDayField.delete(0, END) 
	givenMonthField.delete(0, END) 
	givenYearField.delete(0, END) 
	rsltDayField.delete(0, END) 
	rsltMonthField.delete(0, END) 
	rsltYearField.delete(0, END) 
/////////////////////////////////////
 # untuk mengetahui dan mengecek kesalahan 
def checkError() :  
  
  ////////////////////////////////
  
# jika salah satu bidang entri kosong lalu tampilkan pesan kesalahan dan hapus semua entri

  if (dayField.get() == "" or monthField.get() == "" 
		or yearField.get() == "" or givenDayField.get() == "" 
		or givenMonthField.get() == "" or givenYearField.get() == "") : 

		# tampilkan pesan kesalahan
		messagebox.showerror("Input Error") 

	  # clearAll pemanggilan fungsi
		clearAll() 
		
		return -1

# berfungsi untuk menghitung Umur
def calculateAge() : 

	# mengecek kesalahan 
	value = checkError() 

	# jika terjadi kesalahan kemudian kembali
	if value == -1 : 
		return
	
	else : 
		
		# ambil nilai dari kotak entri masing-masing 
		# dapatkan metode mengembalikan teks saat ini sebagai string 
		birth_day = int(dayField.get()) 
		birth_month = int(monthField.get()) 
		birth_year = int(yearField.get()) 

		given_day = int(givenDayField.get()) 
		given_month = int(givenMonthField.get()) 
		given_year = int(givenYearField.get()) 
		
		
		# jika tanggal lahir lebih besar dari bulan_kelahiran yang diberikan 
		# maka jangan hitung bulan ini dan tambahkan 30 pada tanggal tersebut
		# untuk mengurangi tanggal dan mendapatkan sisa hari 
		month =[31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31] 
		
		if (birth_day > given_day): 
			given_month = given_month - 1
			given_day = given_day + month[birth_month-1] 
					
					
		# jika bulan kelahiran melebihi bulan yang diberikan, maka
		# jangan hitung tahun ini dan tambahkan 12 ke 
		# bulan sehingga kita dapat mengurangi dan mencari tahu perbedaan
    
		if (birth_month > given_month): 
			given_year = given_year - 1
			given_month = given_month + 12
					
		# calculate day, month, year 
		calculated_day = given_day - birth_day; 
		calculated_month = given_month - birth_month; 
		calculated_year = given_year - birth_year; 

		# calculated day, month, year write back 
		# to the respective entry boxes 

		# insert method inserting the 
		# value in the text entry box. 
		
		rsltDayField.insert(10, str(calculated_day)) 
		rsltMonthField.insert(10, str(calculated_month)) 
		rsltYearField.insert(10, str(calculated_year)) 
	

# Driver Code 
if __name__ == "__main__" : 

	# tambahkan GUI window 
	gui = Tk() 

	# Atur warna latar belakang GUI window
	gui.configure(background = "light green") 

	# atur nama tkinter window GUI
	gui.title("Kalkulator Umur") 

	# atur konfigurasi pada GUI window 
	gui.geometry("525x260") 

	# Buat Tanggal Lahir : label 
	dob = Label(gui, text = "Tanggal lahir", bg = "light green") 

	# Buat Tanggal yang Diberikan : label 
	givenDate = Label(gui, text = "Tanggal tertentu", bg = "light green") 

	# Buat Hari yang diberikan : label 
	day = Label(gui, text = "Tanggal", bg = "light green") 

	# Buat Bulan yang diberikan : label 
	month = Label(gui, text = "Bulan", bg = "light green") 

	# Buat Tahun yang diberikan : label 
	year = Label(gui, text = "Tahun", bg = "light green") 

	# Buat Hari yang Ditentukan : label 
	givenDay = Label(gui, text = "hari yang diberikan", bg = "light green") 

	# Buat Bulan yang ditentukan : label 
	givenMonth = Label(gui, text = "bulan ", bg = "light green") 

	# Buat Tahun yang diberikan : label 
	givenYear = Label(gui, text = "Tahun yg diberikan", bg = "light green") 

	# Buat Tahun : label 
	rsltYear = Label(gui, text = "Tahun", bg = "light green") 

	# Buat Bulan : label 
	rsltMonth = Label(gui, text = "Bulan", bg = "light green") 

	# Buat Hari : label 
	rsltDay = Label(gui, text = "hari", bg = "light green") 

	# Buat Tombol Usia yang Dihasilkan dan dilampirkan ke fungsi countAge 
	resultantAge = Button(gui, text = "Umur yang dihasilkan", fg = "Black", bg = "Red", command = calculateAge) 

	# Buat Tombol Hapus Semua dan lampirkan untuk menghapus Semua fungsi 
	clearAllEntry = Button(gui, text = "Hapus Semua", fg = "Black", bg = "Red", command = clearAll) 

	clearAllEntry = Button (gui, text = "Jundi Lesmana",fg = "Black", bg = "light green", command = clearAll)

	# Buat kotak entri teks untuk mengisi atau mengetik informasi. 
	dayField = Entry(gui) 
	monthField = Entry(gui) 
	yearField = Entry(gui) 
	
	givenDayField = Entry(gui) 
	givenMonthField = Entry(gui) 
	givenYearField = Entry(gui) 
	
	rsltYearField = Entry(gui) 
	rsltMonthField = Entry(gui) 
	rsltDayField = Entry(gui) 


	# metode grid digunakan untuk menempatkan
	# # widget di posisi masing-masing dalam tabel seperti struktur.
  
	dob.grid(row = 0, column = 1) 
	
	day.grid(row = 1, column = 0) 
	dayField.grid(row = 1, column = 1) 
	
	month.grid(row = 2, column = 0) 
	monthField.grid(row = 2, column = 1) 
	
	year.grid(row = 3, column = 0) 
	yearField.grid(row = 3, column = 1) 
	
	givenDate.grid(row = 0, column = 4) 
	
	givenDay.grid(row = 1, column = 3) 
	givenDayField.grid(row = 1, column = 4) 
	
	givenMonth.grid(row = 2, column = 3) 
	givenMonthField.grid(row = 2, column = 4) 
	
	givenYear.grid(row = 3, column = 3) 
	givenYearField.grid(row = 3, column = 4) 
	
	resultantAge.grid(row = 4, column = 2) 
	
	rsltYear.grid(row = 5, column = 2) 
	rsltYearField.grid(row = 6, column = 2) 
	
	rsltMonth.grid(row = 7, column = 2) 
	rsltMonthField.grid(row = 8, column = 2) 
	
	rsltDay.grid(row = 9, column = 2) 
	rsltDayField.grid(row = 10, column = 2) 

	clearAllEntry.grid(row = 12, column = 2) 

	# memulai GUI 
	gui.mainloop()	 
