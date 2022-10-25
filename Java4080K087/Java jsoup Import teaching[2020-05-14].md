#  Java jsoup Import teaching
### https://jsoup.org/
```
package org.jsoup.examples;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.IOException;

/**
 * A simple example, used on the jsoup website.
 */
	public class Wikipedia {
		public static void main(String[] args) throws IOException {
			Document doc = Jsoup.connect("http://en.wikipedia.org/").get();
			log(doc.title());

			Elements newsHeadlines = doc.select("#mp-itn b a");
			for (Element headline : newsHeadlines) {
				log("%s\n\t%s", headline.attr("title"), headline.absUrl("href"));
			}
		}

		private static void log(String msg, String... vals) {
			System.out.println(String.format(msg, vals));
		}
}
```
![image](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/My%20Java/Java%5B108-2%5D/image/jsoup.png)
![image](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/My%20Java/Java%5B108-2%5D/image/jsoup1.png)
![image](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/My%20Java/Java%5B108-2%5D/image/jsoup2.png)
![image](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/My%20Java/Java%5B108-2%5D/image/jsoup3.png)
```
package org.jsoup.examples;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.IOException;

/**
 * A simple example, used on the jsoup website.
 */
	public class Wikipedia {
		public static void main(String[] args) throws IOException {
			Document doc = Jsoup.connect("https://rate.bot.com.tw/xrt?Lang=zh-TW").get();
			System.out.println(" 網頁標題： "+doc.title());
			System.out.println(" 網頁網址：= "+doc.baseUri());
			
			Elements trs = doc.select("tr");
			String[] token;
			for(Element tr : trs) {
				token = tr.text().split(" ");
			 for(int i=0 ; i<token.length; i++) {
				 System.out.println(token[i]);
			 }
			}

			//Elements newsHeadlines = doc.select("#mp-itn b a");
			//for (Element headline : newsHeadlines) {
				//log("%s\n\t%s", headline.attr("title"), headline.absUrl("href"));
			//}
		}

		private static void log(String msg, String... vals) {
			System.out.println(String.format(msg, vals));
		}
}
```
