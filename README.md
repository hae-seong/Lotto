# Lotto
로또 숫자를 랜덤으로 보여주어 추천한다.

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Container;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JTextField;

public class Lotto extends JFrame {

	JButton[] jbutton = new JButton[6];
	Container c = getContentPane();
    int[] ab = new int[6];
	Lotto() {
		setTitle("Lotto");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		c.setBackground(Color.GRAY);
		c.setLayout(new GridLayout(2, 3, 0, 0));

		for (int i = 0; i < 6; i++) {
			double randomValue = Math.random();
			int intValue = (int) (randomValue * 45) + 1;

			jbutton[i] = new JButton(Integer.toString(intValue));
			ab[i] = intValue;

			c.add(jbutton[i]);
		//c.add(new JButton(Integer.toString(i)));
		}

		setSize(300, 200);
		setVisible(true);
		c.setLayout(new BorderLayout());
		JButton btn = new JButton("숫자생성");
		add(btn, BorderLayout.SOUTH);
		MyActionListener listener = new MyActionListener();
		btn.addActionListener(listener);

		setSize(300, 227);
		setVisible(true);

	}

	public static void main(String args[]) {
		new Lotto();
	}

	class MyActionListener implements ActionListener {
		public void actionPerformed(ActionEvent e) {
			JButton b = (JButton) e.getSource();
			for (int i = 0; i < 6; i++) {
				double randomValue = Math.random();
				int intValue = (int) (randomValue * 45) + 1;
				ab[i]=intValue;
				for (int j = 0; j <i; j++) {
					if (ab[i]==ab[j]) {
						ab[i]=(int)(randomValue*45)+1;
						i--;
						break;
					} 	
				}
				jbutton[i].setText(Integer.toString(ab[i]));
			//	System.out.println(ab[i]);
				// jbutton[i].setText("test");
			}
			
			
		}
	}

}
