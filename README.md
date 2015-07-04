# Übung 10: Dynamisches Binden

Es soll der in der Vorlesung vorgestellte Mechanismus des Aufrufs von Funktionen in dynamisch gebundenen Bibliotheken nachvollzogen werden. Der nachfolgende C-Programm- ausschnitt, welcher ausnahmsweise für das Betriebssystem *Windows* entwickelt wurde, werde in dieser Aufgabe betrachtet.

	HWND hWnd = CreateWindow ();
	ShowWindow(hWnd);
	UpdateWindow(hWnd);

Die exportierten Symbole aus den für den vorherigen Programmausschnitt benötigten DLLs und die Position der Symbole, relativ zum jeweiligen Modulanfang, ist nachfolgend angegeben.

	user32.dll:
	CreateWindow 0x0000BC2F
	ShowWindow   0x0000BC62
	UpdateWindow 0x00004CC0
	
	kernel32.dll:
	CreateHeap 0x00006472
	HeapAlloc  0x00003438


1. Geben Sie, soweit bekannt, den endgültigen Inhalt und eine Beschreibung der Einträge der *Global Offset Table* (GOT) des obigen Programms an.
2. Wenn das Windows Programm ein Fenster öffnet, muss `CreateWindow()` in `user32.dll` Speicher anfordern, wozu `HeapAlloc()` aufgerufen wird. Geben Sie die GOT von `user32.dll` an. Skizzieren Sie den Ablauf des Aufrufs zum Erzeugen eines Fensters. Nehmen Sie an, dass `user32.dll` an die Adresse `0x00700100` und `kernel32.dll` an die Adresse `0x00900000` geladen wird.
3. Der Mechanismus der GOT wird nun durch Nutzung einer *Procedure Lookup Table* (PLT) erweitert. Wie wird der Aufruf von `CreateWindow()` nun aussehen? Geben Sie die PLT des Programms vor und nach dem ersten Aufruf der Funktion an.
