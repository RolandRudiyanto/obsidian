           IDENTIFICATION DIVISION.

           PROGRAM-ID. Sales.

           ENVIRONMENT DIVISION.

           INPUT-OUTPUT SECTION.

           FILE-CONTROL.

               SELECT SalesFile ASSIGN TO "sales.dat"

                   ORGANIZATION IS LINE SEQUENTIAL.

               SELECT ReportFile ASSIGN TO "commission.dat"

                   ORGANIZATION IS LINE SEQUENTIAL.

  

           DATA DIVISION.

           FILE SECTION.

           FD SalesFile.

           01 SalesRecord.

               05 SalesPerson PIC A(20).

               05 SalesAmount PIC 9(7)V99.

           FD ReportFile.

           01 ReportLine PIC X(80).

  

           WORKING-STORAGE SECTION.

               77 CommissionRate   PIC 9V99 VALUE 0.05.

               77 Commission       PIC 9(7)V99 VALUE 0.

               77 TotalCommission  PIC 9(7)V99 VALUE 0.

               77 DisplayLine      PIC X(80).

               77 EOF              PIC X VALUE "N".

  

           PROCEDURE DIVISION.

               OPEN INPUT SalesFile

               OPEN OUTPUT ReportFile

  

               MOVE "Commission Report" TO DisplayLine

               WRITE ReportLine FROM DisplayLine

               MOVE "-----------------------" TO DisplayLine

               WRITE ReportLine FROM DisplayLine

                   PERFORM UNTIL EOF = "Y"

                   READ SalesFile

                       AT END

                           MOVE "Y" TO EOF

                       NOT AT END

                           COMPUTE Commission = SalesAmount * CommissionRate

                           ADD Commission TO TotalCommission

                           STRING SalesPerson DELIMITED BY SIZE

                                  SPACE

                                  "Sales: " DELIMITED BY SIZE

                                  SalesAmount DELIMITED BY SIZE

                                  SPACE

                                  "Commission: " DELIMITED BY SIZE

                                  Commission DELIMITED BY SIZE

                                  INTO DisplayLine

                           WRITE ReportLine FROM DisplayLine

                   END-READ

               END-PERFORM

  

                   MOVE "-------------------" TO DisplayLine

               WRITE ReportLine FROM DisplayLine

               STRING "Total Commission: " DELIMITED BY SIZE

                      TotalCommission DELIMITED BY SIZE

                      INTO DisplayLine

               WRITE ReportLine FROM DisplayLine

  

                   CLOSE SalesFile

               CLOSE ReportFile

               STOP RUN.
