#MUI
  [MUI����ָ��](http://dev.dcloud.net.cn/mui/ui/)
   >mui.js
   >    (1)��װ�˻������¼��󶨣�ѡ����������(����jQuery)��
   >   (2)���ƶ����¼������˷�װ(tap.swipe),
   >  (3)��װ��WebView��slide�¼���
#H5+
  [H5+Specification API](http://www.html5plus.org/doc/h5p.html)
   > (1)���Native.jsʵ�ֶ�ԭ���˹��ܵĵ���(�Ƚ��ȶ���Ҳ�Ƚ�����)��
   > (2)�ṩ��WebView��������ּ��ɷ�ʽ��
#����������ͽ������
##(1)����WebViewback�¼�����˵��
>�����WebView��д��mui.back()��������ô��WebView��дmui.back()������Ч�����ؼ�������Ĭ����Ϊ�����ȹر���WebView��Ȼ�󴥷���WebView��mui.back()�����������Ҫ����WebViewҳ�����η��ؼ����¼�����������Ҫ����WebViewҳ�棬�������³�ʼ��������
     mui.init({
                keyEventBind: {
                    backbutton: false
                }
      });
     ���óɹ�����WebView�ڽ��յ�back�¼��󣬲���ر�ҳ�棬Ȼ��back�¼��ַ�������WebView��mui.back()������
     
   > ����WebView����WebView���¼��ַ����⣬���緵�ؼ����⣬�������ĵ���������˳����б�ҳ����ʧ����
          mui�ĸ������Ӽ�WebView���¼�������ѭAndroid api�ĸ��ӿؼ����¼����ݻ��ƣ���ѭ���϶��µ��¼��ַ����ơ�������WebView���յ�ϵͳ�¼����������Լ���������������ַ�����WebView��             ������WebView������ѡ�����ѵ����¼�������false������ɸ���WebView������
          
##(2)iOS�汾��ʹ��plus.storage���
  >    iOS�汾�У�storage�����setItem�����޷��洢valueΪ�������͵�ֵ�������Ҫ���棬����Ҫת��Ϊ�ַ������ʹ�����������ʾ��
      plus.storage.setItem(key,value+'');
      Android�汾�в����ڴ����⡣

##(3)mui.backʵ��Ϊwindow.history.back();��Native�˷��ؼ��Ĵ�������H5+ ����������

##(4)�����Ǵ���ڱ������У�������Ajax�Ŀ������⡣

##(5)Angular 
   > \$scope���ݰ󶨲���  \$scope.\$applyAsyncִ�С�(ԭ������controller�ڳ�ʼ���Ĺ����л�Ե�ǰDOM�еı���ʽ���а󶨣������ǰDOM�󶨲�û����ɣ�\$scope��ֱ�Ӹ�ֵ��Ϊ����δ����ɵĹ��̳�ͻ�����°�ʧ�ܣ���\$scope.\$applyAsync�󶨣���֪ͨ�¼��������������Ҫ�����ݣ��������Ŷ�)��

##(6)plus.storage����ṩ��ȫ�ִ洢����������ʵ�ֻ���(ҳ���¼�����)��ȫ�ֱ����洢(״̬��)�ȳ�����

##(7)ҳ���������
   > (1)�����ͬһWebView֮���ҳ����ת����ʹ��QueryString���ƴ��ݣ�Ŀ��ҳ��Ҫʵ��QueryString��������������
    (2)����ǲ�ͬWebView֮��������ݣ�������ʵ�ַ�ʽ��һ������(1)��ͬ��һ����ʹ��WebView��extras��������Ŀ��ҳ�����ֱ������(plus.webview.currentWebView.key)��
    (3)�����������ݣ��������plus.storage.

##(8)����ˢ���б���ʵ�֣�Ϊ�б������ݰ󶨶���ͬһ��ҳ��(���⴦�����ؼ�������)��

##(9)�����б��¼�����
  >   Ĭ������£������ǰ�б������������һҳ(�༴�����޷�ռ����Ļ�����߶�)���򲻻���Ӧ�б����¼�����ʱӦ�����صײ��ġ����ظ��ࡱ�����ʵ�ֵķ���Ϊ��
\$.each(document.querySelectorAll('.mui-slider-group .mui-scroll'), function(index, pullRefreshEl) {
 var loading = document.querySelectorAll('.mui-slider-group .mui-scroll')[index];
$(pullRefreshEl).pullToRefresh({
down: {
 callback: function() {
                          var self = this;
                          console.log("�����¼�����");
                          var currentLoading = loading;
                           //��������¼�
                          window.PFE = 1;
                          refreshData(index);
                          //֪ͨ���ֹͣ����ˢ�²���
                          self.endPullDownToRefresh();
                          if (jQuery(jQuery(currentLoading).children("ul").get(0)).height() <                                jQuery(currentLoading).parent().parent().height()) {
                          //���㵱ǰ��ʾ����߶ȣ��������һҳ��������ʾ�ײ��ġ����ظ��ࡱ
                          self.endPullUpToRefresh(true);
                          } else {
                                     self.endPullUpToRefresh();
                                    }
                          }
                            },
                            up: {
                                auto: true, //auto:true  �Զ�ִ�������¼�һ�Σ�ҳ����أ��Զ�ִ�У�����ִ�У����㵱ǰ��ʾ����߶ȣ��������һҳ��������ʾ�ײ��ġ����ظ��ࡱ��
                                callback: function() {
                                    console.log("�����¼�����");
                                    var self = this;
                                    var currentLoading = loading;
                                    //��������¼�
                                    window.PFE = 2;
                                    refreshData(index);
                                    //�ж��״μ��ص������Ƿ񳬹���ǰ��ʾ����
                                    if (jQuery(jQuery(currentLoading).children("ul").get(0)).height() < jQuery(currentLoading).parent().parent().height()) {
                                        console.log("HJKKLLKL:<L:<L");
                                        self.endPullUpToRefresh(true);
                                    } else {
                                        self.endPullUpToRefresh(false);
                                    }
                                }
                            }
                        });
                    });

  ##(10)�����¼�
> mui.init({
gestureConfig:{
tap:true,//Ĭ��Ϊtrue
doubletap:true,//Ĭ��Ϊfalse
longtap:true,//Ĭ��Ϊfalse
swipe:true,//Ĭ��Ϊtrue
drag:true,//Ĭ��Ϊtrue
hold:false,//Ĭ��Ϊfalse��������
release:false//Ĭ��Ϊfalse��������
}});
## (11)����ʹ��jQuery
 [jQuery API](http://api.jquery.com/)
> (1)�¼��󶨸�Ϊ���㡣
> (2)Ajax�ɿز���Ҳ�϶ࡣ

## (12)Angular ���ݰ�
[Angular API](https://docs.angularjs.org/api)
> View�㣺����һ�����ص�button������angular.element("#updateNoticeCount").trigger('click');����ʽ���������ݼ��غͰ󶨡�

## (13)Angular��DOM��Ĳ�������
> ����ҳ���HTMLԪ��֮�⡣����ʹ��window����(Angular��controller��ͨ��DI��ע��$window����,�༴DOM�е�window����)��������Ҫ��ҳ���б����س�����

##  (14)ʵ�ְ�ѹ����Ԫ����ʽ���������ʹ�����·���(��Ҫ��hold��release�¼�)��
> mui('.mui-bar-tab').on('hold', 'a', function(e) {
                //��ס��Ļ
                jQuery(this).removeClass('mui-active');
                jQuery(this).addClass('mui-active');
            });
            mui('.mui-bar-tab').on('release', 'a', function(e) {
                //�뿪��Ļ
                jQuery(this).removeClass('mui-active');
            });   

## (15)����ˢ�³���
> ����ˢ�³���������˵������ҳ�����б�ҳ�ĳ����У���������mui.init({beforeback:function(){}}),����Ҫ�ڷ��ؼ�����ʱ���һЩ����(rerurn true:�����ִ�з��ؼ��������̣�return false:����ֹ��                   �ؼ���������)���ٴ˻ص��п���ʵ��ˢ����һ��WebView���ݵĹ��ܡ�

## (16)HTMLҳ����a��ǩ��href���Դ���
 > �����#����tap�¼��е�event���󣬲�������ֹð�ݡ���Ϊjavascript:void(0)���߱������ɶ���У��Ϳ��Ե���event�����preventDefault����stopPropagation��ֹĬ����Ϊ��

## (17) mui.fire()
> ���Ҫ������һ�� WebView���¼�����ʹ��mui.fire().���ͳ���Ϊ���໬���ܵ�ʵ�֣��漰�໬ҳ����ҳ�档

## (18)ͼƬ�����ڵĲ����쳣
> ���ҳ���д���ͼƬչʾ�ĳ����������ǰͼƬ���ӵ�ַ��Ч(����˵ͼƬ������)��MUIĬ�ϵ���ʽ�����ҳ�沼�֣��������岼���쳣�����������������
                1.����js��image�����onerror�¼��ڼ�⵽�¼�����ʱ����˵��ͼƬ��ַ��Ч����ʱ����ɾ��DOM�еĸ�imgԪ�ء�
                2.��imgԪ������Ĭ�ϵĴ�С

## (19)plus.nativeUI.showWaiting();
> ��ʹҳ�������¼�����������(��������������ԣ���ҳ���޷�����������ȴ�ִ����ɣ�ִ�йر�plus.nativeUI.closeWaiting();)

## (20)backbutton
> ����backbuttonΪfalse,��ʾ��ǰWebView���������ؼ������ֵĽ��Ϊ����ǰWebView�Է��ؼ�����Ӧ��ֻ�����������ؼ����¼��ַ������к��Ե�ǰWebView�����ؼ� ����ԭ���¼����ݻ��ơ�
    > mui.init({
                keyEventBind: {
                    backbutton: false
                }
      });

## (21)plus.runtime.openURL()�������ñ������������URL��

## (22)plus.runtime.launchApplication()���Դ򿪱�����װ��APP��

## (23)�����ʾ���ѡ����ѡ���ʴ����js��������֯�ͽӿڴ�������
> ��jsģ��java��bean��ArrayList�Ĵ������ݵ���ʽ�洢��ѡ����ѡ���ʴ���Ĵ𰸣���"|"�ָ��������ͣ���","�ָ�ѡ�������ַ������䣬����˰��ռȶ���ʽ�ָ��洢��
    >> Tips:ʹ��JavaScriptʵ���������
     (1)�������([Immutable.js](https://facebook.github.io/immutable-js/))
     (2)����ʽ���([jQuery](http://api.jquery.com/))
## (24)ѡ��л���ҳ�����������ݼ�������
> ѡ���href="#"��Ӧģ���div��id�������пո�
���ݼ���ʱmui.plusReady֮�󣬴���Angular JS��controller�������ݣ���Ҫ��˻�����£������������������ݡ�

## (25)mui�������ط�ҳ����Ӧ����
> muiĬ��������б����ݳ�����Ļʱ������Ӧ�������ص����ƣ���Ҫ�޸�mui-pull����ʽ

## (26)����л�Ч������ȷ����
> ������Angular Js��ng-repeat������Ҫ�Ĺ������֮�⣬��mui-slider-group mui-slider-loop��ǩ֮����Ҫ�ֶ����ӹ��ĵ�һ������һ������[list.length-1]--�������--���[0]

## (27)�����б���������
> ����ҳ�Ĺ����̻ᣬ��Ŀ�ƹ��
> �ӿ��ڲ�ѯ�б�ʱ��Ҫ�ݹ�����һ���б������ظ��ͻ��ˣ��ͻ��˾������ص�ҳ�棬ֱ��û����һ���б�Ϊֹ

## (28)�������ص�һҳ�����û����ҳ���ݺ�������ǩ��ʾû�и�����������
> ��Ҫ�Զ�������ҳ������ʾ������ʾ

## (29)֪ͨ�����桢�����ʾ���ͶƱ״̬��������
> ֪ͨ�������Ŀ��Ҫ����δ�����Ѷ������ύ״̬������֪ͨ��Ŀ��Ҫ�����Ƿ�Ͳ�ȷ������״̬�����ܻ��� 