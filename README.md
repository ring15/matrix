# matrix

Main.java
package Operation;
import Random.Random_matrix;//调用随机产生矩阵的包
import java.util.Random;//产生随机数
import java.util.Scanner;//输入


public class Main {
	public static void show(double[][] c){
		for(int j=0;j<c.length;j++){
			for(int i=0;i<c[0].length;i++){
				System.out.print(c[j][i]+"\t");
			}
			System.out.println();
		}
	}//输出双精度浮点型矩阵
	public static void main(String[] args) {
		 //TODO Auto-generated method stub
		Scanner inp=new Scanner(System.in);
		System.out.print("选择矩阵输入方式：【随机生成（1），手动输入（2）】");
		int z=inp.nextInt();
		if(z==1){
			int length1,length2,length3;
			Random ran=new Random();
			length1=(int)(ran.nextInt(5)+1);//随机产生一系列行长和列长
			length2=(int)(ran.nextInt(5)+1);
			length3=(int)(ran.nextInt(5)+1);
			double a[][]=new double[length1][length2];
			double p[][]=new double[length1][length2];
			double b[][]=new double[length2][length3];
			double e[][]=new double[length1][length1];
			double f[][]=new double[length1][length1];
			double d[][]=new double[a.length][a[0].length];
		    double w[][]=new double[e.length][e[0].length];
		    double q[][]=new double[e.length][e[0].length];
		    Scanner input=new Scanner(System.in); 
		    System.out.print("输入要进行的运算（+、-、*、/、~（逆）：");//输入要进行的运算
		    String s=input.next();
		    input.close();
		    char c=s.charAt(0);
		    switch(c){    //判断运算方法
		    case '+':
		    a=Random_matrix.divide_inverse_matrix(length1, length2);//函数返回值为随机产生的矩阵
		    p=Random_matrix.divide_inverse_matrix(length1, length2);
		    System.out.println("输出矩阵a：");//分别输出两个中间过程矩阵
		    show(a);
		    System.out.println("输出矩阵p：");
		    show(p);
		    d=Plus.add(a, p);//返回得到的结果——求过和之后的矩阵
		    	System.out.println("输出相加后的矩阵c：");
		    	show(d);
		    break;
		    case '-':   //大体同加法
		    a=Random_matrix.divide_inverse_matrix(length1, length2);
			p=Random_matrix.divide_inverse_matrix(length1, length2);
		    System.out.println("输出矩阵a：");
		    show(a);
		    System.out.println("输出矩阵p：");
		    show(p);
		    d=Minus.minus(a, p);
		    System.out.println("输出相减后的矩阵d：");
		    show(d);
		    break;
		    case '*':   //同上
		    a=Random_matrix.divide_inverse_matrix(length1, length2);
			b=Random_matrix.divide_inverse_matrix(length2, length3);
		    System.out.println("输出矩阵a：");
		    show(a);
		    System.out.println("输出矩阵b：");
		    show(b);
		    d=Multiply.multiply_d(a, b);
		    System.out.println("输出相乘后的矩阵d：");
		    show(d);
		    break;
		    case '/':
		    e=Random_matrix.divide_inverse_matrix(length1, length1);//能进行除法运算的必须是方阵
		    f=Random_matrix.divide_inverse_matrix(length1, length1);
		    System.out.println("输出矩阵f：");
		    show(f);
		    System.out.println("输出矩阵e：");
		    show(e);
		    w=Divide.divide_inverse(e);//要求除法，先求逆
		    q=Multiply.multiply_d(f, w);//求逆以后两式进行乘法运算
		    System.out.println("f除e后的矩阵q：");
		    show(q);
		    break;
		    case '~':
		    e=Random_matrix.divide_inverse_matrix(length1, length1);
		    System.out.println("输出矩阵w：");
		    show(e);
		    w=Divide.divide_inverse(e);
		    System.out.println("输出逆矩阵~w：");
		    show(w);
		    break;
		    default :System.out.println("输入错误！"); break;
		    }
		}
		else if(z==2){//手动输入数组
			int ah,al,bh,bl;
			Scanner inpu=new Scanner(System.in); 
			System.out.print("请输入矩阵A的行数："); 
			ah=inpu.nextInt(); 
			System.out.print("请输入矩阵A的列数："); 
			al=inpu.nextInt(); 
			System.out.print("请输入矩阵B的行数："); 
			bh=inpu.nextInt(); 
			System.out.print("请输入矩阵B的列数："); 
			bl=inpu.nextInt(); 
			double a[][]=new double [ah][al]; 
			double b[][]=new double [bh][bl];
			double d[][]=new double[ah][al];
			double f[][]=new double[ah][bl];
			double p[][]=new double[ah][ah];
			double q[][]=new double[ah][ah];
			Scanner input=new Scanner(System.in); 
			for(int i=0;i<a.length;i++){ //输入矩阵a
				for(int j=0;j<a[i].length;j++) { 
					System.out.print("输入矩阵a的["+i+"] ["+j+"]:"); 
					a[i][j]=input.nextInt(); 
				} 
			} 
			System.out.println(); 
			System.out.println("输出矩阵a:");
			for(int i=0;i<a.length;i++){ //输出a
				for(int j=0;j<a[i].length;j++) { 
					System.out.print(a[i][j]+" ");
				}
				System.out.println();
			}
			for(int i=0;i<b.length;i++){ //输入矩阵b
				for(int j=0;j<b[i].length;j++) { 
					System.out.print("输入矩阵b的["+i+"] ["+j+"]:"); 
					b[i][j]=input.nextInt(); 
				} 
			} 
			System.out.println(); 
			System.out.println("输出矩阵b:");
			for(int i=0;i<b.length;i++){ //输出b
				for(int j=0;j<b[i].length;j++) { 
					System.out.print(b[i][j]+" ");
				}
				System.out.println();
			}
			System.out.print("请输入要进行的算法：" );
			String s=inpu.next();
			char c=s.charAt(0);
			switch(c){
			case '+':
				if(ah==bh&al==bl){//能相加的矩阵需要满足的条件
					d=Plus.add(a,b);
					System.out.println("输出相加后的矩阵：");
					show(d);
				}
				else{
					throw new IllegalArgumentException("这两个矩阵不能相加!");//抛出异常
				}
				break;
			case '-':
				if(ah==bh&al==bl){//相减的条件，与相加一致
				    d=Minus.minus(a, b);
					System.out.println("输出相减后的矩阵：");
					show(d);
				}
				else{
					throw new IllegalArgumentException("这两个矩阵不能相减!");
				}
			    break;
			case '*':
				if(al==bh){//相乘
				    f=Multiply.multiply_d(a, b);
					System.out.println("输出相乘后的矩阵：");
					show(f);
				}
				else{
					throw new IllegalArgumentException("这两个矩阵不能相乘!");
				}
			    break;
			case '/':
				if(ah==al&al==bh&bh==bl){//除法运算必须为方阵
					p=Divide.divide_inverse(b);
					q=Multiply.multiply_d(a, p);
					System.out.println("输出相除后的矩阵(a/b)：");
					show(q);
				}
				else{
					throw new IllegalArgumentException("这两个矩阵不能相除!");
				}
			    break;
			case '~':
				if(ah==al){//求可逆矩阵的逆矩阵
					p=Divide.divide_inverse(b);
					System.out.println("输出b求逆后的矩阵：");
					show(p);
				}
				else{
					throw new IllegalArgumentException("此矩阵不能求逆!");
				}
			    break;
			default:
				System.out.println("选择错误！");
			}

		}
		else
			System.out.println("选择错误！");

    }

}

Plus.java
package Operation;

public class Plus {

	public static double[][] add(double[][] a,double[][] b){
		double[][] c = new double[a.length][a[0].length];
		for(int i=0;i<a.length;i++){
			for(int j=0;j<a[0].length;j++){
				c[i][j]=a[i][j]+b[i][j]; //两个矩阵的对应项相加，得到矩阵相加后的矩阵
			}
		}
		return c;
	}
	
}
Minus.java
package Operation;

public class Minus {
	public static double[][] minus(double[][] a,double[][] b){
		double[][] c = new double[a.length][a[0].length];
		for(int i=0;i<a.length;i++){
			for(int j=0;j<a[0].length;j++){
				c[i][j]=a[i][j]-b[i][j]; //与加法运算几乎一样，这里把‘+’变为‘-’
			}
		}
		return c;
	}

}

Multiply.java
package Operation;


public class Multiply {

	public static double[][] multiply_d(double[][] a,double[][] b){//双精度浮点型的乘法
		double[][] c = new double[a.length][b[0].length];
		for(int i=0;i<a.length;i++){
			for(int j=0;j<b[0].length;j++){
				for(int m=0;m<a[0].length;m++){
					c[i][j]+=a[i][m]*b[m][j];//矩阵a的每一行对应的a.length个数分别乘b的每一列对应的b[0].length个数，再求和
				} 
			}
		}
		return c;//返回的c是一个a.length*b[0].length的方阵
	}

}

Divide.java
package Operation;

public class Divide {
	public static double[][] divide_inverse(double b[][]){
		double[][] c=new double[b.length][b.length];
		double[][] inv=new double[b.length][2*b.length];
		double[][] inv2=new double[b.length][2*b.length];
		double m;
		for(int i=0;i<2*b.length;i++){//将b和一个单位矩阵相连
			if(i<b.length)
				for(int j=0;j<b.length;j++)
					inv[j][i]=b[j][i];
			else{
				for(int j=0;j<b.length;j++)
					if(i==j+b.length)
						inv[j][i]=1;//对角线上的为1，其余为0
					else
						inv[j][i]=0;
			}
		}
		inv2=inv;
		for(int i=0;i<b.length-1;i++){//等式进行行变换，前半部分变成上三角矩阵
			for(int z=1;z<b.length-i;z++){
				if(Math.abs(inv[z+i][i])>=1e-5){
				m=inv[i][i]/inv[z+i][i];//m为进行行变换的两行第一个不为0的数的商
				for(int j=i;j<2*b.length;j++){
					inv2[z+i][j]=m*inv[z+i][j]-inv[i][j];//变换后的值放入一个新的矩阵中
					}
				}
				else continue;//当需要行变换的行中与上一个行变换后的第一个不为0的数的列相同时，若该数为0，则跳过此行的行变换
				}
		}
		inv=inv2;
		for(int i=b.length-1;i>0;i--){//继续进行行变换，至前半部分变为类似的单位矩阵（对角数字不一定为1）
			for(int z=i-1;z>=0;z--){
				if(Math.abs(inv[z][i])>=1e-5){
				m=inv[i][i]/inv[z][i];//同上
				for(int j=2*b.length-1;j>=0;j--){
					inv2[z][j]=m*inv[z][j]-inv[i][j];
					}
				}
				else continue;//同上
				}
		}
		inv=inv2;
		for(int i=0;i<b.length;i++){
			if(Math.abs(inv[i][i])>=1e-5){//将矩阵的前半部分变为单位矩阵
			m=inv[i][i];
			for(int j=0;j<2*b.length;j++)
				inv2[i][j]=inv[i][j]/m;
			}
			else{
				throw new IllegalArgumentException("该矩阵不可逆!");
			}
		}
		for(int i=b.length;i<2*b.length;i++){
			for(int j=0;j<b.length;j++)
				c[j][i-b.length]=inv2[j][i];//遍历矩阵的后半部分即得到矩阵的逆矩阵
		}
		return c;
	}

}

Random_matrix.java
package Random;
import java.util.Random;//随机数

public class Random_matrix {

	public static double[][] divide_inverse_matrix(int length1,int length2){//（双精度浮点型）
		double c[][]=new double[length1][length2];
		Random ran=new Random();
		for(int i=0;i<length1;i++)
			for(int j=0;j<length2;j++)
				c[i][j]=ran.nextInt(10);//随机产生矩阵中的每一个元素
		return c;
	}

}
