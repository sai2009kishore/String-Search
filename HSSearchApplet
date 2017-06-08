import java.applet.*;
import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.util.*;
/*<applet code="HSSearchApplet.class" width="500" height="500"></applet>*/
public class HSSearchApplet extends Applet implements ActionListener
{
	static String aa="";
	static int total;
	static int i=0;
	static Label l1,l2,l3;
	static Button b,b1;
	static TextField enterVal,compl,tot;
	static TextArea ta;
	static int found=0;
	static HashSet<String> hset;
	public void init()
	{
		try
		{
			ObjectInputStream ois=new ObjectInputStream(new FileInputStream(new File("mainobj.txt")));
			HSMainObject mm=(HSMainObject)ois.readObject();
			hset=mm.hs;
			l1=new Label("String:");
			l2=new Label("of");
			l3=new Label("Completed");
			b=new Button("Search");
			b1=new Button("Clear");
			enterVal=new TextField(10);
			compl=new TextField(6);
			tot=new TextField(6);
			ta=new TextArea();
			b.addActionListener(this);
			add(l1);
			add(enterVal);
			add(b);
			add(ta);
			add(l3);
			add(compl);
			add(l2);
			add(tot);
			add(b1);
			b1.addActionListener(this);
		}
		catch(Exception e){e.printStackTrace();}
	}
	
	public void paint(Graphics g)
	{
		setBackground(Color.ORANGE);
		l1.setBackground(Color.ORANGE);
		l2.setBackground(Color.ORANGE);
		l3.setBackground(Color.ORANGE);
	}

	public void actionPerformed(ActionEvent e)
	{
		if(e.getActionCommand()=="Clear")
		{
			ta.setText("");
			compl.setText("");
			tot.setText("");
			aa="";
		}
		else
		{
		try
		{
			
			String str=enterVal.getText();
			total=1;
			i=0;
			found=0;
			for(int j=1;j<=str.length();j++)
				total*=j;
			tot.setText(total+"");
			permutation("",str);
			enterVal.setText("");
			if(found==0)
				aa+="Sorry! No word found in dictionary.";
			else
			aa+="Completed! Found "+found+" word(s) in dictionary.\n";
			ta.setText(aa);
		}
		catch(IOException sd){}
		}
	}
		
	
	public static void permutation(String prefix, String str) throws IOException
	{
		int n = str.length();
		if (n == 0)
		{
			i++;
			compl.setText(i+"");
			BufferedReader br=new BufferedReader(new FileReader("words.txt"));
				if(hset.contains(prefix.toLowerCase()))
				{
					aa+=prefix+"\n";
					ta.setText(aa);
					found++;
				}
			br.close();
		}
		else 
		{	
			for (int i = 0; i < n; i++)
				permutation(prefix + str.charAt(i), str.substring(0, i) + str.substring(i+1, n));
		}
	}
}
