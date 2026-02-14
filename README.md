# ADO.Netlearning
Day3: (Connected Architecture)
=====
SQL Connection Class :
=====================
  if the crentidals is known then go for the  Integrated security using window authentication

  SqlConncection con= new SqlConnection()

Sqlcommand class:
=================
 Sqlcommand cmd =new Sqlcommand("select * from customer",con)

 using execute query we can able to make
 Method of execute
 =================
  Int I= cmd.ExecutenonQuery(); --> for which doesn't return any record  ( int is used for how many is affected)
  SqlDataReader dr=cmd.ExecuteReader(); --> for which return any record
  XMLDataReader dr =cmd.ExceuteXMLReader(); --> for XML files
  Object ob=cmd.Executescalar(); --> gives a single value

  the steps in involeved in 
  Imports namespaces
  Create conncection object
  Open Connection
  Create command object 
  Execute 
  Extract 


  Transcation
  ===========
  Roll back and commit
  Transcation always uses multiple query

  some examples for doing the transcation
  ======================================
    SqlTransaction tr = null;



  try
  {

      SqlConnection con = new SqlConnection("Integrated security=true;server=WIN2019;database=db0902");
      con.Open();
    tr =  con.BeginTransaction();

      SqlCommand cmd1 = new SqlCommand("insert into TableA values(1,'aa')",con);
      cmd1.Transaction= tr;
      SqlCommand cmd2 = new SqlCommand("insert into TableB values(1,'aa')", con);
      cmd2.Transaction = tr;

      cmd1.ExecuteNonQuery();
      cmd2.ExecuteNonQuery();
      tr.Commit();

      con.Close();
      Console.WriteLine("Transaction happens successfully!!!");
  }
  catch(Exception ex)
  {
      tr.Rollback();
      Console.WriteLine("Transaction rollbacked");
  }

Basic SQL SERVER works
======================
create table empolyee
(
empid int primary key,
empname varchar(20),
doj date,
salary int
)

select * from empolyee

insert into empolyee values(100,'Manikandan','1-1-2004',50000);
insert into empolyee values(101,'Alosius','1-1-2005',60000);
insert into empolyee values(102,'vignesh','1-1-2006',50000);
insert into empolyee values(103,'Akash','1-1-2004',500000);

delete  from empolyee where empid=106

=============================================================

Procedure
==========
create procedure showemp
as 
select * from empolyee

showemp


create procedure showempname(@a varchar(20))
as 
select * from empolyee where empname = @a

showempname 'Manikandan'

alter procedure showempname(@a varchar(20))
as 
select * from empolyee where empname like @a+'%'

showempname 'v'



=======================================================================

Day 4:(Disconnected Architeture)
===============================
All CRUD operation are performed offline

classes are

Sqlconnection 
SqlDataAdaptor --> holds the sql commands and conncetion (only class interact with the database)
DataSet        --> holds the result dataset(multiple table) (in memory representation)
DataTable      --> holds the result dataset(single table)
DataRow        --> holds the single row 
DataColumn     --> holds the sibgle column



diff b/n the sqlDataReader and DataSet
=======================
SqlDataReader                                 DataSet
=======                                       
connection is required                        not needed
Read Only                                     Read/Write
Forward only                                  forward/backward
Single Table                                  Multiple
is database specific class                    shared class



