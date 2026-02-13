# ADO.Netlearning


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
  Roll back and commit
  Transcation always uses multiple query
==============================================================================================================
  some examples for doing the transcation
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
=================================================================================================================
