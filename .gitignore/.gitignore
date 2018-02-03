import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.ServerSocket;
import java.net.Socket;

public class Server {
    public static void main(String[] args) throws IOException{
        Server socketService = new Server();
        socketService.oneServer();
    }
    public  void oneServer(){
        try{
            ServerSocket server=null;
            try{
                server=new ServerSocket(5209);
                System.out.println("服务器启动成功");
            }catch(Exception e) {
                System.out.println("没有启动监听："+e);
            }
            Socket socket=null;
            try{
                socket=server.accept();
            }catch(Exception e) {
                System.out.println("Error."+e);
            }
            String line;
            BufferedReader in=new BufferedReader(new InputStreamReader(socket.getInputStream()));
            PrintWriter writer=new PrintWriter(socket.getOutputStream());
            BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
            System.out.println("Client:"+in.readLine());
            line=br.readLine();
            while(!line.equals("end")){
                writer.println(line);
                writer.flush();
                System.out.println("Server:"+line);
                System.out.println("Client:"+in.readLine());
                line=br.readLine();
            }
            writer.close();
            in.close();
            socket.close();
            server.close();
        }catch(Exception e) {
            System.out.println("Error."+e);
        }
    }
}
