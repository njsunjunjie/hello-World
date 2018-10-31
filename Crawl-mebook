#coding=utf-8
import requests
from lxml import etree
import time

#url='http://mebook.cc/'
urer_agent='Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.26 Safari/537.36 Core/1.63.6756.400 QQBrowser/10.2.2457.400'
hd={'User-Agent': urer_agent}

def get_url_Page(url):
      r=requests.get(url,headers=hd,timeout=30)
      wp=etree.HTML(r.text)
      objs=wp.xpath('//div[@class="content "]/h2/a/@href')
      #print(objs)

      two_urls=[]
      for obj in objs:
            two_html=requests.get(obj)
            two_wp=etree.HTML(two_html.text)
            two_objs=two_wp.xpath('//a[@class="downbtn"]/@href')
            if two_objs==[]:
                  continue
            else:
                  i=two_objs[0]
                  two_urls.append(i)
      #print(two_urls)
           
      c=[]
      for obj in two_urls:

            three_html=requests.get(obj)
            three_wp=etree.HTML(three_html.text)
            name=three_wp.xpath('//div[3]/p[1]/text()')
            a=name[0].split('《')
            
            print(a[1][:-1])      
            three_url=three_wp.xpath('//div[5]/a[1]/@href')
            print(three_url[0])      
            mm=three_wp.xpath('//div[3]/p[6]/text()')
            b=mm[0].split('：')
            print(b[2][0:4])
            c=[a[1][:-1],three_url[0],b[2][0:4]]
            for d in c:
                  f= open(r'd:\mypython\xiaoshuwu3.txt','a',encoding='utf-8')
                  line=d +'\n'
                  f.writelines(line)
                  f.close()

#get_url_Page(url)                  
def main():           
      for page in range(301,401):
            url = 'http://mebook.cc/page/' + str(page)
            print(page)
            get_url_Page(url)
            time.sleep(2)

if __name__=='__main__':
      
      main()
