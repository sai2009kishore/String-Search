import java.util.*;
import java.io.*;
class HSMainObject implements Serializable
{
	HashSet<String> hs;
}
class HSCreateObject implements Serializable
{
	public static void main(String args[]) throws Exception
	{
		HSMainObject m=new HSMainObject();
		m.hs=new HashSet<String>();
		File f=new File("words.txt");
		File f1=new File("mainobj.txt");
		BufferedReader br=new BufferedReader(new FileReader(f));
		String st="";
		while((st=br.readLine())!=null)
			m.hs.add(st);
		ObjectOutputStream oos=new ObjectOutputStream(new FileOutputStream(f1));
		oos.writeObject(m);
		oos.flush();
	}
}	
