# ms

```
import java.net.*;
public class EchoServer {
  public static void main(String[] a) throws Exception {
    DatagramSocket s = new DatagramSocket(1234);
    byte[] buf = new byte[1024];
    DatagramPacket p = new DatagramPacket(buf, buf.length);
    s.receive(p);
    String msg = new String(p.getData(), 0, p.getLength());
    InetAddress ip = p.getAddress();
    int port = p.getPort();
    s.send(new DatagramPacket(msg.getBytes(), msg.length(), ip, port));
    s.close();
  }
}

```

```
import java.net.*; import java.util.*;
public class EchoClient {
  public static void main(String[] a) throws Exception {
    DatagramSocket s = new DatagramSocket();
    Scanner sc = new Scanner(System.in);
    System.out.print("Enter msg: "); String msg = sc.nextLine();
    InetAddress ip = InetAddress.getByName("localhost");
    s.send(new DatagramPacket(msg.getBytes(), msg.length(), ip, 1234));
    byte[] buf = new byte[1024];
    DatagramPacket p = new DatagramPacket(buf, buf.length);
    s.receive(p);
    System.out.println("From Server: " + new String(p.getData(), 0, p.getLength()));
    s.close();
  }
}

```
