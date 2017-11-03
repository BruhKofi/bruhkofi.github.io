---
layout: post
title: "Größten
Gemeinsamen Teilers Zweier Positiver Ganzer Zahlen in Java"
date: "2017-11-03 03:00:10 +0100"
blog: true
author: kofi
image: /assets/images/Blog/java-logo.png
tag:
  - tech
  - ggt
  - java
  - grundlagen der programmierung
  - code
comments: true
description: Experimentierung mit eclipse und dem Java-Compiler/-Interpreter und implementierung dabei den Eukidischen Algorithmus zur Bestimmung des groeßten gemeinsamen Teilers zweier positiver ganzer Zahlen in Java.
permalink: /blog/:categories/groessten-gemeinsamen-teiler-java/
categories: Tech
---


![Java Logo](/assets/images/Blog/java-logo.png)


Experimentieren Sie mit eclipse und dem Java-Compiler/-Interpreter (wie unten erläutert) und implementieren Sie dabei den Eukidischen Algorithmus <http://de.wikipedia.org/wiki/Euklidischer_Algorithmus> <euklid> zur Bestimmung des größten gemeinsamen Teilers zweier positiver ganzer Zahlen in Java.



Erstellen Sie (ggf. in einem neuen eclipse-Projekt) ein Java-Programm GGT.java, welches (in Anlehnung an die Berechnung der Summe zweier Zahlen)
den größten gemeinsamen Teiler von zwei positiven ganzen Zahlen nach dem Euklidischen Algorithmus berechnet und ausgibt.
Das Prinzip des euklidischen Algorithmus wird auch gegenseitige Wechselwegnahme genannt. Eingangsgrößen seien zwei positive ganze Zahlen a und
b. Bei der Berechnung verfährt man nach Euklid wie folgt:


Überzeugen Sie sich durch geeignete Tests von der Korrektheit Ihrer Implementation. Versuchen Sie auch den Algorithmus strukturell so zu formulieren,
dass man die obige verbale Beschreibung wiedererkennen kann. Sorgen Sie dafür, dass im Programm geprüft wird, ob die beiden als Argumente
übergebenden Zahlen tatsächlich positiv (also >0) sind. Ansonsten funktioniert der oben beschriebene Ablauf vielleicht gar nicht richtig!? Das macht man
in Java üblicherweise so:

{% highlight java %}
 if (irgendwassIstFaul) {
 System.out.println("eine passende Ausschrift");
 System.exit(-1); // Programmm sofort beenden
 // negative Parameter weisen den Rufer
 // auf ein abnormales Ende hin
 }
    {% endhighlight %}

Abschließend hier noch ein paar Beispielaufrufe, die zeigen, wie sich Ihr Programm verhalten soll - offenbar müssen Sie sich NICHT darum kümmern,
dass tatsächlich zwei Zahlen als Argumente übergeben werden.

{% highlight java %}
$ java GGT 12 14
ggT(12, 14) = 2
$ java GGT 36 12
ggT(36, 12) = 12
java GGT 36 -12
nur positive ganze Zahlen als Argumente erlaubt
$ java GGT -36 12
nur positive ganze Zahlen als Argumente erlaubt
$ java GGT 666
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1
 at GGT.main(GGT.java:6)
$ java GGT 6 sieben
Exception in thread "main" java.lang.NumberFormatException: For input string: "sieben"
 at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
 at java.lang.Integer.parseInt(Integer.java:492)
 at java.lang.Integer.parseInt(Integer.java:527)
 at GGT.main(GGT.java:6)
 {% endhighlight %}


{% highlight java %}

public class GGT {

	public static void main(String s[]) {
		// eingaben akzeptieren
		int a = Integer.parseInt(s[0]);
		int b = Integer.parseInt(s[1]);
		
		// falls eine die eingegebene Zahlen a und b ein negativer Zahl ist, ein error message ergeben
		if ((a < 0) || (b <  0) ) {
			System.out.println( "nur positive ganze Zahlen als Argumente erlaubt");
		}
		
		//setze m = a und n = b und initialisiert c und r als integers
		int m = a;
		int n = b;
		int c;
		int r;

		/* sei m < n, dann wird die beide vertauscht 
		 * dann r = m - n
		 * setze dann m = n, n = r
		 * */ 
		if (m < n) {
			c = m;
			m = n;
			n = c;
			
			r = m - n;
			//ist r nicht gleich 0, fortfahren  ab line 15
			if (r != 0){
				System.out.println("ggt(" + m +", " + n + ") = " + r );
			}

		}
		

	}

}
{% endhighlight %}
