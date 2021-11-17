**CONTENT BEYOND SYLLABUS**                                                                                                              Sharwin Xavier R - 311119205050<br />
                                                       **IMPLEMENTATION OF REMOTE COMMAND EXECUTION (RCE)**<br />


**AIM**<br />
  
  To implement Remote Command Execution(RCE).<br />

**ALGORITHM**<br />
  
  **CLIENT SIDE**<br />
      1. Establish a connection between the Client and Server.<br />
      Socket client=new Socket("127.0.0.1",6555);<br />
      2. Create instances for input and output streams.
      Print Stream ps=new Print Stream(client.getOutputStream());<br />
      3. BufferedReaderbr=newBufferedReader(newInputStreamReader(System.in));<br />
      4. Enter the command in Client Window.<br />
      Send themessage to its output<br />
      str=br.readLine();<br />
      ps.println(str);<br />
  
  **SERVER SIDE**<br />
      1. Accept the connection request by the client.<br />
      ServerSocket server=new ServerSocket(6555);<br />
      Sockets=server.accept();<br />
      2. Getthe IPaddressfromitsinputstream.<br />
      BufferedReaderbr1=newBufferedReader(newInputStreamReader(s.getInputStream()));<br />
      ip=br1.readLine();<br />
      3. During runtime execute the process<br />
      Runtime r=Runtime.getRuntime();<br />
      Process p=r.exec(str);<br />

**CLIENT PROGRAM**<br />
      import java.io.*;<br />
      import java.net.*;<br />
      class clientRCE<br />
      {<br />
      public static void main(String args[]) throws IOException<br />
      {<br />
      try<br />
      {<br />
      String str;Socket client=new Socket("127.0.0.1",6555);<br />
      PrintStream ps=new PrintStream(client.getOutputStream());<br />
      BufferedReader br=new BufferedReader(new InputStreamReader(System.in));<br />
      System.out.println("\t\t\t\tCLIENT WINDOW\n\n\t\tEnter TheCommand:");<br />
      str=br.readLine();<br />
      ps.println(str);<br />
      }<br />
      catch(IOException e)<br />
      {<br />
      System.out.println("Error"+e); }<br />
      }<br />
      }<br />

**SERVER PROGRAM**<br />
      
      import java.io.*;<br />
      import java.net.*;<br />
      class serverRCE<br />
      {<br />
      public static void main(String args[]) throws IOException<br />
      {<br />
      try<br />
      {<br />
      String str;<br />
      ServerSocket server=new ServerSocket(6555);<br />
      Socket s=server.accept();<br />
      BufferedReader br=new BufferedReader(new InputStreamReader(s.getInputStream()));<br />
      str=br.readLine();<br />
      Runtime r=Runtime.getRuntime();<br />
      Process p=r.exec(str);<br />
      }<br />
      catch(IOException e)<br />
      {<br />
      System.out.println("Error"+e);<br />
      }<br />
      }<br />
      }<br />

**OUTPUT**<br />
    C:\NetworkingPrograms>java serverRCE<br />
    C:\NetworkingPrograms>java clientRCE<br />
    CLIENT WINDOW<br />
    EnterTheCommand:<br />
    Notepad<br />
    ![Output Screenshot](https://user-images.githubusercontent.com/65103675/142233316-57f4bf0b-4b0a-4079-b078-3fa7b6f6caab.jpg)<br />


**RESULT**<br />
    Thus the implementation RCE is done & executed successfully.<br />
