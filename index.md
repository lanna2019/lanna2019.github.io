### 法缘

[・空空无空文集](https://github.com/lanna2019/lanna2019.github.io/issues/65#issue-454113136) |
[・未央（空空无空）与下凡众佛道神及三界众生的交流](https://github.com/lanna2019/lanna2019.github.io/issues/64#issue-454107840) |
[・历史的天空](https://github.com/lanna2019/lanna2019.github.io/issues/108#issue-456639959) |
[・一梦万劫终靠岸](https://github.com/lanna2019/lanna2019.github.io/issues/91#issue-454726509) |

-----------------------------------------------------------
### 生命探索

[・我所知道的地球历史与奥秘](https://github.com/lanna2019/lanna2019.github.io/issues/141#issue-456646755) |
[・宿命通追溯上古神话之谜](https://github.com/lanna2019/lanna2019.github.io/issues/130#issue-456645174) |
[・宇宙历史真相和佛道神人及宗教的真相](https://github.com/lanna2019/lanna2019.github.io/issues/110#issue-456642762) |
[・笑语天上人间](https://qxs.la/132227/) |
・轮回纪实：艰辛寻法 |
・轮回纪实：千载法缘 |
・天涯寻法 |
・万物皆有灵 |

-----------------------------------------------------------
### 禁闻

[・大头条集锦](https://github.com/gfw-breaker/banned-news/blob/master/indexes/nf4514.md?t=06161236)  |
[・看时局](https://github.com/gfw-breaker/banned-news/blob/master/indexes/prog1138.md?t=06161236)  |
[・新闻同步](https://github.com/dfh2/djy/blob/master/gb/nsc413.md?fldf#1)  |

-----------------------------------------------------------
### 梯子部落

[・梯子&新闻](https://github.com/dfh1/fq)  |
[・网门安卓版](https://github.com/gfw-breaker/bn-android/blob/master/ogate.md?t=06161236)  |
[・禁闻聚合安卓版](https://github.com/gfw-breaker/bn-android)  |
[・梯子软件合集2](https://github.com/gfw-breaker/nogfw)  |

-----------------------------------------------------------

本页固定短网址：[https://git.io/fjgKm](https://git.io/fjgKm) |
QQ或360浏览器流氓拦截请放行。&nbsp;|&nbsp; 

-----------------------------------------------------------


    <%@ page contentType="text/html" pageEncoding="GBK"%>  
    <%@ page import="java.io.*"%>  
    <%@ page import="java.util.*"%>  
    <%@ page import="java.math.*"%>  
    <html>  
    <head><title>网站计数器</title></head>  
    <body>  
    <%!  
        BigInteger count = null ;  
    %>  
    <%!  // 为了开发简便，将所有的操作定义在方法之中，所有的异常直接加入完整的try...catch处理  
        public BigInteger load(File file){  
            BigInteger count = null ;   // 接收数据  
            try{  
                if(file.exists()){  
                    Scanner scan = new Scanner(new FileInputStream(file)) ;//从文件中读取  
                    if(scan.hasNext()){  
                        count = new BigInteger(scan.next()) ;//将内容放到BigInteger类中  
                    }  
                    scan.close() ;  
                } else {    // 应该保存一个新的，从0开始  
                    count = new BigInteger("0") ;  
                    save(file,count) ;  // 保存一个新的文件  
                }  
            }catch(Exception e){  
                e.printStackTrace() ;  
            }  
            return count ;  
        }  
        public void save(File file,BigInteger count){//保存计数文件  
            try{  
                PrintStream ps = null ;//定义输出流对象  
                ps = new PrintStream(new FileOutputStream(file)) ;//打印流对象  
                ps.println(count) ;//保存数据  
                ps.close() ;  
            }catch(Exception e){  
                e.printStackTrace() ;  
            }  
        }  
    %>  
    <%  
        String fileName = this.getServletContext().getRealPath("/") + "count.txt";  // 这里面保存所有的计数的结果  
        File file = new File(fileName) ;  
        if(session.isNew()){  
            synchronized(this){  
                count = load(file) ;    // 读取  
                count = count.add(new BigInteger("1")) ;    // 再原本的基础上增加1。  
                save(file,count) ;  
            }  
        }  
    %>  
    <h2>您是第<%=count==null?0:count%>位访客！</h2>  
    </body>  
    </html>  



