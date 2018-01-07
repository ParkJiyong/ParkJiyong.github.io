---
layout: post
title: "Java Product"
description: Made by PARKJIYONG in hanyang univ.
image: 'http://cfile4.uf.tistory.com/image/24103833576616351AE6E7.jpg'
category: 'Portfolio'
twitter_text: Java Product
introduction: Product in the first year
---

Execution results
---
![Main display](/assets/img/main.png){: width="300" height="300"}
**Game that can earn money will be added.**


![Shop display](/assets/img/shop.png)
**Users can buy some furnitures here.**
**More furnitures will be added.**
**Users can choose color themselves by RGB table.**


![After display](/assets/img/after.png)


![Move display](/assets/img/move.png)
**Users can move and replace the furnitures.**



***
**code below**

First Java class
---

```
package project;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.Image;
import java.awt.Toolkit;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;

public class myproject extends JPanel {
	private Image im;
	public static int wallcheck;
	public static int picturecheck;
	public static int rectcheck;
	public static int ovalcheck;
	public static int flowercheck;
	static int bank_balancee=99999999;
	static int wallR;
	static int wallG;
	static int wallB;
	static int ovalR;
	static int ovalG;
	static int ovalB;
	static int rectR1,rectG1,rectB1,rectR2,rectG2,rectB2;
	static int wr,wg,wb,or,og,ob,rr1,rg1,rb1,rr2,rg2,rb2;
	static int pp,rp,op,fp;
	static int flo,pic,rec,ova,pf,rf,of,ff,ppx,opy;

	public myproject() {
		flowercheck = myprojectshop.flowercheck;
		ovalcheck = myprojectshop.ovalcheck;
		rectcheck = myprojectshop.rectcheck;
		picturecheck = myprojectshop.picturecheck;
		wallcheck = myprojectshop.wallcheck;
		bank_balancee = myprojectshop.bank_balance;
		wallR = myprojectshop.wallR;
		wallG = myprojectshop.wallG;
		wallB = myprojectshop.wallB;
		ovalR = myprojectshop.ovalR;
		ovalG = myprojectshop.ovalG;
		ovalB = myprojectshop.ovalB;
		rectR1 = myprojectshop.rectR1;
		rectG1 = myprojectshop.rectG1;
		rectB1 = myprojectshop.rectB1;
		rectR2 = myprojectshop.rectR2;
		rectG2 = myprojectshop.rectG2;
		rectB2 = myprojectshop.rectB2;
		wr = wallR;
		wg = wallG;
		wb = wallB;
		or = ovalR;
		og = ovalG;
		ob = ovalB;
		rr1 = rectR1;
		rg1 = rectG1;
		rb1 = rectB1;
		rr2 = rectR2;
		rg2 = rectG2;
		rb2 = rectB2;
		pp = myprojectshop.picturedot;
		rp = myprojectshop.rectdot;
		op = myprojectshop.ovaldot;
		fp = myprojectshop.flowerdot;
		ppx = myprojectshop.picturedotx;
		opy = myprojectshop.ovaldoty;
		//System.out.println(flowercheck);
		if (myprojectmove.pf != 0)
			pp = myprojectmove.pic;
		if (myprojectmove.rf != 0)
			rp = myprojectmove.rec;
		if (myprojectmove.of != 0)
			op = myprojectmove.ova;
		if (myprojectmove.ff != 0)
			fp = myprojectmove.flo;
		if (myprojectmove.pf != 0)
			ppx = myprojectmove.picx;
		if (myprojectmove.of != 0)
			opy = myprojectmove.opy;
		
		if (ppx<206)
			ppx = 206;
		if (ppx>412)
			ppx = 412;
		if (pp<50)
			pp = 50;
		if (pp>210)
			pp = 210;
		if (op<210)
			op = 210;
		if (op>219)
			op = 219;
		if (opy<210)
			opy = 210;
		if (opy>230)
			opy = 230;
		
		//System.out.println(fp);
		//System.out.println(myprojectmove.ff);
		//System.out.println(wb);
		JFrame f = new JFrame();
		setLayout(null);
		f.getContentPane().add(this);
		f.setBounds(0, 0, 550, 500);
		f.setTitle("JAVA WORLD");
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//상점버튼
		JButton jb = new JButton("SHOP");
		jb.setSize(90, 40);
		jb.setLocation(412, 410);
		add(jb);
		jb.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				f.setVisible(false);
				new myprojectshop();
			}
		});
		//이동버튼 
		JButton jb1 = new JButton("MOVE");
		jb1.setSize(90, 40);
		jb1.setLocation(412, 360);
		add(jb1);
		jb1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				f.setVisible(false);
				new myprojectmove();
			}
		});
		//잔고안내 
		JLabel balance = new JLabel(" YOUR BANK BALANCE : "+ bank_balancee);
		balance.setSize(400, 60);
		balance.setLocation(50, 400);
		add(balance);
		
		
		f.setVisible(true);
	}

	public void make_basic_room(Graphics g) {
		g.setColor(Color.white);
		g.fillRect(0, 0, 550, 500);
		g.setColor(Color.black);
		//g.drawLine(206, 50, 412, 50);
		g.drawLine(206, 50, 137, 100);
		g.drawLine(137, 100, 137, 260);
		//g.drawLine(412, 50, 412, 210);
		//g.drawLine(206, 50, 206, 210);
		//g.drawLine(206, 210, 412, 210);
		g.drawRect(206, 50, 206, 160);
		g.drawLine(206, 210, 137, 260);
		g.drawLine(343, 260, 412, 210);
		g.drawLine(343, 260, 137, 260);
		// g.drawLine(412, 50, 343, 100);
		// g.drawLine(343, 100, 137, 100);
	}

	public void showpicture(int x, int z, Graphics g) {
		im = Toolkit.getDefaultToolkit().getImage("/Users/parkjiyong/Desktop/pic.jpeg");
		g.drawImage(im, x, z, 50, 50, this);
	}

	public void showflower(int flower_point,Graphics g) {
		// 화분
		g.setColor(new Color(102, 051, 000));
		g.fillRect(flower_point, flower_point+54, 30, 7);
		int e[] = new int[] { flower_point+5, flower_point+25, flower_point+23, flower_point+7 };
		int f[] = new int[] { flower_point+61, flower_point+61, flower_point+75, flower_point+75 };
		g.fillPolygon(e, f, e.length);
		// 줄기
		g.setColor(new Color(051, 153, 051));
		g.fillRect(flower_point+14, flower_point+46, 4, 8);
		// 꽃잎
		g.setColor(Color.pink);
		g.fillOval(flower_point+11, flower_point+31, 10, 10);
		g.fillOval(flower_point+16, flower_point+34, 10, 10);
		g.fillOval(flower_point+16, flower_point+41, 10, 10);
		g.fillOval(flower_point+6, flower_point+41, 10, 10);
		g.fillOval(flower_point+6, flower_point+34, 10, 10);
		g.setColor(Color.yellow);
		g.fillOval(flower_point+11, flower_point+36, 10, 10);
	}

	public void floor_rect(int rect_point,int q,int w, int e,int r, int t, int y,Graphics g) {
		int base_x[] = new int[] { rect_point, rect_point+164, rect_point+124, rect_point-40 };
		int base_y[] = new int[] { rect_point+4, rect_point+4, rect_point+34, rect_point+34 };
		g.setColor(new Color(q, w, e));
		g.fillPolygon(base_x, base_y, base_x.length);

		g.setColor(new Color(r, t, y));
		int paint_x1[] = new int[] { rect_point+27, rect_point+54, rect_point+14, rect_point-13 };
		int paint_y1[] = new int[] { rect_point+4, rect_point+4, rect_point+34, rect_point+34 };
		g.fillPolygon(paint_x1, paint_y1, paint_x1.length);
		int paint_x2[] = new int[] { rect_point+81, rect_point+108, rect_point+68, rect_point+41 };
		int paint_y2[] = new int[] { rect_point+4, rect_point+4, rect_point+34, rect_point+34 };
		g.fillPolygon(paint_x2, paint_y2, paint_x2.length);
		int paint_x3[] = new int[] { rect_point+136, rect_point+164, rect_point+124, rect_point+96 };
		int paint_y3[] = new int[] { rect_point+4, rect_point+4, rect_point+34, rect_point+34 };
		g.fillPolygon(paint_x3, paint_y3, paint_x3.length);
	}

	public void floor_oval(int j, int k, int l,int ovalx,int ovaly, Graphics g) {
		g.setColor(new Color(j, k, l));
		g.fillOval(ovalx, ovaly, 124, 30);
	}

	public void wallcolor(int x, int y, int z, Graphics g) {
		g.setColor(new Color(x, y, z));
		g.fillRect(207, 51, 205, 159);
		// 평행사변형
		g.fillRect(138, 100, 68, 110);
		int a[] = new int[] { 139, 206, 206 };
		int b[] = new int[] { 100, 51, 100 };
		g.fillPolygon(a, b, a.length);
		int c[] = new int[] { 138, 205, 138 };
		int d[] = new int[] { 210, 210, 259 };
		g.fillPolygon(c, d, c.length);
	}

	public void paintComponent(Graphics g) {
		make_basic_room(g);
		if (wallcheck!=0) {
			wallcolor(wr, wg, wb, g);
		}
		if (picturecheck!=0) {
			showpicture(ppx,pp, g);
		}
		if (rectcheck!=0) {
			floor_rect(rp,rr1, rg1, rb1, rr2, rg2, rb2,g);
		}
		if (ovalcheck!=0) {
			floor_oval(or, og, ob,op,opy,g);
		}
		if (flowercheck!=0) {
			showflower(fp,g);
		}
		

	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//String password_real = "parkjiyong";
		//String password_input = JOptionPane.showInputDialog("Input ur NAME : ");
		//while (!password_input.equals(password_real)) {
			//JOptionPane.showMessageDialog(null,"CAN'T FIND");
			//password_input = JOptionPane.showInputDialog("Input ur NAME : ");
		//}
		new myproject();
	}

}
```

Second Java class
---

```
package project;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.Image;
import java.awt.Toolkit;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class myprojectshop extends JPanel {
	private Image im0;
	private Image im1;
	private Image im2;
	private Image im3;
	public static int wallcheck = 0 ;
	public static int picturecheck = 0;
	public static int rectcheck = 0;
	public static int ovalcheck = 0;
	public static int flowercheck = 0;
	static int bank_balance=99999999;//=잔고
	static int wallR;
	static int wallG;
	static int wallB;
	static int ovalR;
	static int ovalG;
	static int ovalB;
	static int rectR1,rectG1,rectB1,rectR2,rectG2,rectB2;
	static int picturedot=100,rectdot=216,ovaldot=216,flowerdot=176,picturedotx=280,ovaldoty=220;;
	
	private Image im;
	JLabel cwc = new JLabel(" CHANGE WALL COLOR ");
	JTextField cwc_color1 = new JTextField(3);
	JTextField cwc_color2 = new JTextField(3);
	JTextField cwc_color3 = new JTextField(3);
	JButton wallmoney = new JButton(" $400 ");
	JLabel pictureframe = new JLabel(" PICTURE FRAME ");
	JButton picturemoney = new JButton(" $100 ");
	JLabel carpetrect = new JLabel(" CARPET_RECT ");
	JTextField rectcolor1 = new JTextField(3);
	JTextField rectcolor2 = new JTextField(3);
	JTextField rectcolor3 = new JTextField(3);
	JTextField rectcolor4 = new JTextField(3);
	JTextField rectcolor5 = new JTextField(3);
	JTextField rectcolor6 = new JTextField(3);
	JButton rectmoney = new JButton(" $250 ");
	JLabel carpetoval = new JLabel(" CARPET_OVAL ");
	JTextField ovalcolor1 = new JTextField(3);
	JTextField ovalcolor2 = new JTextField(3);
	JTextField ovalcolor3 = new JTextField(3);
	JButton ovalmoney = new JButton(" $200 ");
	JLabel flower = new JLabel(" FLOWER_POT ");
	JButton flowermoney = new JButton(" $100 ");
	JLabel balance = new JLabel(" YOUR BANK BALANCE : "+ bank_balance );
	
	
	
	
	public myprojectshop(){
		//wallcheck = 0;
		//picturecheck = 0;
		//rectcheck = 0;
		//ovalcheck = 0;
		//flowercheck = 0;
		//System.out.println(bank_balance);
		JFrame j = new JFrame();
		setLayout(null);
		j.getContentPane().add(this);
		j.setBounds(0, 0, 550, 500);
		j.setTitle("JAVA WORLD - SHOP");
		j.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//벽색깔 
		cwc.setSize(350, 40);
		cwc.setLocation(50, 50);
		add(cwc);
		cwc_color1.setSize(36, 30);
		cwc_color1.setLocation(275, 50);
		add(cwc_color1);
		cwc_color2.setSize(36, 30);
		cwc_color2.setLocation(311, 50);
		add(cwc_color2);
		cwc_color3.setSize(36, 30);
		cwc_color3.setLocation(347, 50);
		add(cwc_color3);
		wallmoney.setSize(120, 40);
		wallmoney.setLocation(417, 50);
		wallmoney.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				bank_balance = bank_balance - 400;
				wallcheck = wallcheck + 1;
				String awallR = cwc_color1.getText();
				wallR = new Integer(awallR).intValue();
				if (awallR =="")
					wallR = myproject.wr;
				
				
				String awallG = cwc_color2.getText();
				wallG = new Integer(awallG).intValue();
				if (awallG =="")
					wallG = myproject.wg;
				
				
				String awallB = cwc_color3.getText();
				wallB = new Integer(awallB).intValue();
				if (awallB =="")
					wallB = myproject.wb;
				
				
				System.out.println("Wall color will be drawn");
			}
		});
		add(wallmoney);
		//액자걸기 
		pictureframe.setSize(350, 40);
		pictureframe.setLocation(50, 90);
		add(pictureframe);
		picturemoney.setSize(120, 40);
		picturemoney.setLocation(417, 90);
		picturemoney.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				bank_balance = bank_balance - 100;
				picturecheck = picturecheck + 1;
				picturedot = 100;
				myprojectmove.pf = 0;
				System.out.println("A Picture will be drawn on the wall");
			}
		});
		add(picturemoney);
		//사각카펫 
		carpetrect.setSize(350, 40);
		carpetrect.setLocation(50, 150);
		add(carpetrect);
		rectcolor1.setSize(36, 30);
		rectcolor1.setLocation(275, 135);
		add(rectcolor1);
		rectcolor2.setSize(36, 30);
		rectcolor2.setLocation(311, 135);
		add(rectcolor2);
		rectcolor3.setSize(36, 30);
		rectcolor3.setLocation(347, 135);
		add(rectcolor3);
		rectcolor4.setSize(36, 30);
		rectcolor4.setLocation(275, 160);
		add(rectcolor4);
		rectcolor5.setSize(36, 30);
		rectcolor5.setLocation(311, 160);
		add(rectcolor5);
		rectcolor6.setSize(36, 30);
		rectcolor6.setLocation(347, 160);
		add(rectcolor6);
		rectmoney.setSize(120, 40);
		rectmoney.setLocation(417, 150);
		rectmoney.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				bank_balance = bank_balance - 250;
				rectcheck = rectcheck + 1;
				rectdot = 216;
				myprojectmove.rf = 0;
				String arectR1 = rectcolor1.getText();
				rectR1 = new Integer(arectR1).intValue();
				if (arectR1 =="")
					rectR1 = myproject.rr1;
				
				
				String arectG1 = rectcolor2.getText();
				rectG1 = new Integer(arectG1).intValue();
				if (arectG1 =="")
					rectG1 = myproject.rg1;
				
				
				String arectB1 = rectcolor3.getText();
				rectB1 = new Integer(arectB1).intValue();
				if (arectB1 =="")
					rectB1 = myproject.rb1;
				
				
				String arectR2 = rectcolor4.getText();
				rectR2 = new Integer(arectR2).intValue();
				if (arectR2 =="")
					rectR2 = myproject.rr2;
				
				
				String arectG2 = rectcolor5.getText();
				rectG2 = new Integer(arectG2).intValue();
				if (arectG2 =="")
					rectG2 = myproject.rg2;
				
				
				String arectB2 = rectcolor6.getText();
				rectB2 = new Integer(arectB2).intValue();
				if (arectB2 =="")
					rectB2 = myproject.rb2;
				
				
				System.out.println("A Rectangle carpet will be drawn");
			}
		});
		add(rectmoney);
		//원형카펫 
		carpetoval.setSize(350, 40);
		carpetoval.setLocation(50, 210);
		add(carpetoval);
		ovalcolor1.setSize(36, 30);
		ovalcolor1.setLocation(275, 210);
		add(ovalcolor1);
		ovalcolor2.setSize(36, 30);
		ovalcolor2.setLocation(311, 210);
		add(ovalcolor2);
		ovalcolor3.setSize(36, 30);
		ovalcolor3.setLocation(347, 210);
		add(ovalcolor3);
		ovalmoney.setSize(120, 40);
		ovalmoney.setLocation(417, 210);
		ovalmoney.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				bank_balance = bank_balance - 200;
				ovalcheck = ovalcheck + 1;
				ovaldot = 216;
				myprojectmove.of = 0;
				String aovalR = ovalcolor1.getText();
				ovalR = new Integer(aovalR).intValue();
				if (aovalR =="")
					ovalR = myproject.or;
				
				String aovalG = ovalcolor2.getText();
				ovalG = new Integer(aovalG).intValue();
				if (aovalG =="")
					ovalG = myproject.og;
				
				String aovalB = ovalcolor3.getText();
				ovalB = new Integer(aovalB).intValue();
				if (aovalB =="")
					ovalB = myproject.ob;
				
				System.out.println("An Oval carpet will be drawn");
			}
		});
		add(ovalmoney);
		//화분 
		flower.setSize(350, 40);
		flower.setLocation(50,250);
		add(flower);
		flowermoney.setSize(120, 40);
		flowermoney.setLocation(417, 250);
		flowermoney.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				bank_balance = bank_balance - 100;
				flowercheck = flowercheck + 1;
				flowerdot = 176;
				myprojectmove.ff = 0;
				System.out.println("A Flower pot will be drawn");
			}
		});
		add(flowermoney);
		//뒤로가기 
		JButton back = new JButton("BACK");
		back.setSize(90, 40);
		back.setLocation(412, 360);
		add(back);
		back.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				j.setVisible(false);
				new myproject();
			}
		});
		balance.setSize(400, 60);
		balance.setLocation(50, 400);
		add(balance);
		j.setVisible(true);
	}
	public void showpicture(Graphics g) {
		im0 = Toolkit.getDefaultToolkit().getImage("/Users/parkjiyong/Desktop/c1.jpeg");
		im1 = Toolkit.getDefaultToolkit().getImage("/Users/parkjiyong/Desktop/c2.jpeg");
		im2 = Toolkit.getDefaultToolkit().getImage("/Users/parkjiyong/Desktop/c3.jpeg");
		im3 = Toolkit.getDefaultToolkit().getImage("/Users/parkjiyong/Desktop/c4.jpeg");
		g.drawImage(im0, 560, 0, 400, 500, this);
		g.drawImage(im1, 960, 0, 400, 500, this);
		g.drawImage(im2, 1360, 0, 400, 500, this);
		g.drawImage(im3, 1760, 0, 400, 500, this);
		
	}

	
	public void paintComponent(Graphics g) {
		g.setColor(Color.white);
		g.fillRect(0, 0, 550, 500);
		g.setColor(Color.black);
		g.drawString("R", 292, 35);
		g.drawString("G", 328, 35);
		g.drawString("B", 364, 35);
		showpicture(g);
		
	}

	public static void main(String[] args) {
		// TODO Auto-generated method s
	}

}
```

Third Java class
---

```
package project;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class myprojectmove extends JPanel{
	JTextField towhere = new JTextField(3);
	JTextField howmuch = new JTextField(3);
	JTextField what = new JTextField(10);
	static int howmuch1;
	static int picture_point;
	static int rect_point;
	static int oval_point;
	static int flower_point,picture_pointx,oval_pointy;
	static int picture_f=0;
	static int rect_f=0;
	static int oval_f=0;
	static int flower_f=0;
	static int flo,pic,rec,ova,pf,rf,of,ff,picx,opy;
	
	public myprojectmove() {
		picture_point = myproject.pp;
		rect_point = myproject.rp;
		oval_point = myproject.op;
		flower_point = myproject.fp;
		picture_pointx = myproject.ppx;
		oval_pointy = myproject.opy;
		JFrame h = new JFrame();
		setLayout(null);
		h.getContentPane().add(this);
		h.setBounds(0, 0, 550, 500);
		h.setTitle("JAVA WORLD - MOVE");
		h.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//텍스트 필드 
		what.setSize(120, 40);
		what.setLocation(50, 340);
		add(what);
		towhere.setSize(45, 40);
		towhere.setLocation(245, 340);
		add(towhere);
		howmuch.setSize(45, 40);
		howmuch.setLocation(350, 340);
		add(howmuch);
		//버튼
		JButton b = new JButton("BACK");
		b.setSize(90, 40);
		b.setLocation(312, 410);
		add(b);
		b.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				h.setVisible(false);
				new myproject();
			}
		});
		JButton jb = new JButton("APPLY");
		jb.setSize(90, 40);
		jb.setLocation(412, 410);
		add(jb);
		jb.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				String what1 = what.getText();
				String towhere1 = towhere.getText();
				String how = howmuch.getText();
				howmuch1 = new Integer(how).intValue();

				if (what1.equals("picture frame")) {
					if (towhere1.equals("w")) picture_point-=howmuch1;
					else if (towhere1.equals("a")) picture_pointx-=howmuch1;
					else if (towhere1.equals("s")) picture_point+=howmuch1;
					else if (towhere1.equals("d")) picture_pointx+=howmuch1;
					++picture_f;
				}
				else if (what1.equals("carpet_rect")) {
					if (towhere1.equals("w")) rect_point-=howmuch1;
					else if (towhere1.equals("a")) rect_point-=howmuch1;
					else if (towhere1.equals("s")) rect_point+=howmuch1;
					else if (towhere1.equals("d")) rect_point+=howmuch1;
					++rect_f;
				}
				else if (what1.equals("carpet_oval")) {
					if (towhere1.equals("w")) oval_pointy-=howmuch1;
					else if (towhere1.equals("a")) oval_point-=howmuch1;
					else if (towhere1.equals("s")) oval_pointy+=howmuch1;
					else if (towhere1.equals("d"))oval_point+=howmuch1;
					++oval_f;
				}
				else if (what1.equals("flower_pot")) {
					if (towhere1.equals("w")) flower_point-=howmuch1;
					else if (towhere1.equals("a")) flower_point-=howmuch1;
					else if (towhere1.equals("s")) flower_point+=howmuch1;
					else if (towhere1.equals("d")) flower_point+=howmuch1;
					++flower_f;
					//System.out.println("pass");
				}
				//System.out.println(what1);
				//System.out.println(towhere1);
				//System.out.println(how);
				//System.out.println(flower_point);
				//System.out.println(flower_f);
				opy = oval_pointy;
				picx = picture_pointx;
				pic = picture_point;
				rec = rect_point;
				ova = oval_point;
				flo = flower_point;
				pf = picture_f;
				rf = rect_f;
				of = oval_f;
				ff = flower_f;
				System.out.println("applied");
				//h.setVisible(false);
				//new myproject();
			}
		});

		h.setVisible(true);
	}
	
	public void make_basic_room(Graphics g) {
		g.setColor(Color.white);
		g.fillRect(0, 0, 550, 500);
		g.setColor(Color.black);
		//g.drawLine(206, 50, 412, 50);
		g.drawLine(206, 50, 137, 100);
		g.drawLine(137, 100, 137, 260);
		//g.drawLine(412, 50, 412, 210);
		//g.drawLine(206, 50, 206, 210);
		//g.drawLine(206, 210, 412, 210);
		g.drawRect(206, 50, 206, 160);
		g.drawLine(206, 210, 137, 260);
		g.drawLine(343, 260, 412, 210);
		g.drawLine(343, 260, 137, 260);
		// g.drawLine(412, 50, 343, 100);
		// g.drawLine(343, 100, 137, 100);
	}
	
	public void makeline(Graphics g) {
		g.fillRect(137, 290, 275, 3);
		g.drawLine(137, 285, 137, 298);
		g.drawLine(412, 285, 412, 298);
		g.drawLine(147, 285, 147, 298);
		g.drawLine(187, 285, 187, 298);
		g.drawLine(237, 285, 237, 298);
		g.drawLine(337, 285, 337, 298);
	}
	
	public void paintComponent(Graphics g) {
		make_basic_room(g);
		makeline(g);
		g.drawString("Object", 50, 330);
		g.drawString("toWhere", 245, 330);
		g.drawString("Howmuch", 350, 330);
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}

}
```
