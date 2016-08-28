//# stack_in_applets
//this is a code in java to implement stack visually using applets
package Applets;
import java.applet.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Scanner;
public class Stack extends Applet implements ActionListener {
	
	private static final long serialVersionUID = 1L;
	Node head=null;
	
	int x,n,k=0;
	String s;
	int c=50;
	
	TextField t1,t2;
	Button b1,b2,b3;

	public void init()
		{
	// setBackground(Color.black);
	//	  setForeground(Color.white);
		     t1=new TextField(5);
		     t2=new TextField(10);
		     b1=new Button("Push");
			 b2=new Button("Pop");
			 b3=new Button("Count");
			
			}
	public void start()
		{
		    add (t1);
		    add (t2);
			add (b1);
			add (b2);
			add (b3);
			b1.addActionListener(this);
			b2.addActionListener(this);
			b3.addActionListener(this);
		}
	public void actionPerformed(ActionEvent ae)
		{
			s=ae.getActionCommand();
			Action();
		}
	public void Action() 
		{
			int i,j,k;
			   i=s.compareTo("Push");
			   j=s.compareTo("Pop");
			   k=s.compareTo("Count");
			   if(i==0)
					{
						push();
					}
			   if(j==0)
					{
				   pop();
					}
			   if(k==0)
					{
				   		 count();
					}
		
		    }
		

	
	public void paint(Graphics g)
		{
		
          Node tmp=head;
          for(int i=0;i<k;i+=20)
			{
				g.drawRect(300, 300+i , 50, 20);
				g.drawString(""+tmp.n, 320, i+315);
			    tmp=tmp.next;
			}
		}
	void Display()
	{
		k=c*20;
		repaint();
	 }
	@SuppressWarnings("unused")
	void push()
	{
		Node tmp= new Node();
		c++;
		x=Integer.parseInt(t1.getText());
		
		if(tmp==null)
		{
			t2.setText("Memory Full");
		}
		else
		{
			tmp.n=x;
			tmp.next=null;
			if(head==null)
			{
				head=tmp;
			}
			else
			{	
				tmp.next=head;
				head=tmp;
			}
		}
	Display();
	}
	void pop()
	{
		Node tmp=head;
		c--;
		if(head==null);
		
		else
		{
			tmp=head;
				head=head.next;
				t2.setText("Popping "+tmp.n);
				tmp.next=null;
		        tmp=null;	
			
		}
	Display();
	}
	
	void count()
	{
		int count=0;
		Node cnt=head;
		if(head==null)
			count=0;
		else
		{
			while(cnt!=null)
			{
				count++;
				cnt=cnt.next;
				
			}
		}
		t2.setText(""+count );
		
	}
	
}

	  
	


