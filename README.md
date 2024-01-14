// Bài tập tuần 2
//Họ tên Nguyễn Việt Hoàng CNTT 1504 MSV 1571020108

Bài 1 
package javaapplication1.tuan2;

// Tạo và quản lý luồng
public class MyThread extends  Thread {

    @Override
    public void run() {
         System.out.println("luồng đang chạy ");
    }
    public static void main(String[] args) {
        MyThread th=new MyThread ();
        th.start();
    }
    
}





 Bài 2 

 
package javaapplication1.tuan2;
public class DaLuong {
    public static void main(String[] args) {
        // gọi luồng
        Thread th1=new Thread(new DNRunable("Luồng 1 "));
        th1.start();
        
        Thread th2=new Thread(new DNRunable("Luồng 2 "));
        th2.start();
    }
 }
class DNRunable implements Runnable {
private String threadName; // Quản lý theo tên 
// hàm khởi tạo 
       public DNRunable(String name) {
        this.threadName=name; 
        }
    
    @Override
    public void run() {
        System.out.println("(Băt đầu thực hiện công việc trong"
       + threadName);
        //Thực hiện công việc trong
        for (int i = 0; i <= 5; i++) 
        {
            System.out.println(threadName + ";Bước "+i );
            try {
                Thread.sleep(1000); //ngủ
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        System.out.println("(kết thúc công việc)");
}
}





bài 3 
package javaapplication1.tuan2;

public class VongDonLuong {
    public static void main(String[] args) {
     //tạo một luồng mới
     Thread th1=new Thread(new DNRunable2());
     // bắt đầu luồng
     th1.start();
     //chờ 
        try {
            Thread.sleep(2000);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    // ngừng
    
}
class DNRunable2 implements Runnable{
    @Override
    public void run() {
        System.out.println("(Luồng đang chạy - Trạng thái)"
        +Thread.currentThread().getState());
        try {
            Thread.sleep(5000);// nghỉ 5s
        } catch (Exception e) {
            System.out.println("(Luồng bị ngắt ngủ - Trạng thái )"
            +Thread.currentThread().getState() );
        }
        System.out.println("(Luồng đã kết thúc - Trạng thái)"
        +Thread.currentThread().getState());
    }

}
