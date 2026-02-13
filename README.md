# ADO.Netlearning


SQL Connection Class :
  if the crentidals is known then go for the  Integrated security using window authentication

  SqlConncection con= new SqlConnection()

Sqlcommand class:

 Sqlcommand cmd =new Sqlcommand("select * from customer",con)

 using execute query we can able to make
 Method of execute
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
