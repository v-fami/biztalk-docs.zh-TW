---
title: "如何執行服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, client applications
- service solution tutorial, starting solution
- service solution tutorial, sending requests
- service solution tutorial, SOAP transports
ms.assetid: 764a5ddc-e571-41d8-9e2f-6d0fb3361b2f
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35c33b914ecbb9f385e5546d100b7572b4b48b6a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-run-the-service-oriented-solution"></a>如何執行服務導向解決方案
下列步驟描述如何在單一電腦上執行和驗證服務導向解決方案。 啟動付款追蹤器模擬器之後，使用 SOAP 或 MQSeries 傳輸來傳送要求 (服務導向解決方案的配接器與內嵌版本分別使用個別程序)。  
  
-   [使用用戶端應用程式 （虛設常式版本） 透過 SOAP 傳輸傳送要求](#step1)  
  
-   [使用用戶端應用程式 （配接器版本） 傳送要求](#step3)  
  
-   [使用用戶端應用程式 （內嵌版本） 傳送要求](#step5)  
  
##  <a name="step1"></a>使用用戶端應用程式 （虛設常式版本） 透過 SOAP 傳輸傳送要求  
  
#### <a name="to-send-requests-by-soap-transport-using-the-client-application-stub-version"></a>使用用戶端應用程式 (虛設常式版本) 透過 SOAP 傳輸傳送要求  
  
1.  開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。  
  
2.  輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。  
  
3.  輸入任何 16 位數的數字中**帳戶號碼**文字方塊。  
  
4.  選取**SOAP (WS Call)**和**虛設常式**中**選取傳輸與參數**群組方塊。  
  
5.  輸入下列 URL 中的**URL**文字方塊中，例如：  
  
6.  `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub/CustomerServicePort.asmx`  
  
7.  型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
8.  型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
9. 按一下**取得我的平衡**。  
  
10. 回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。  
  
     ![執行虛設常式版本的用戶端應用程式](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")  
  
##  <a name="step3"></a>使用用戶端應用程式 （配接器版本） 傳送要求  
  
#### <a name="to-send-requests-using-the-client-application-adapter-version"></a>使用用戶端應用程式 (配接器版本) 傳送要求  
  
1.  開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug，然後執行下列命令以啟動付款追蹤器模擬器：  
  
     `BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*佇列管理員名稱* `> 5 [<` *通道定義*`>]`  
  
    > [!NOTE]
    >  若不是 MQSeries Server，則通道定義為選擇性。  
  
    -   讓付款追蹤器模擬器繼續執行。  
  
2.  開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。  
  
3.  在 BTSScnSOSimpleClient.exe 中，使用下列方式透過 SOAP 傳輸傳送要求：  
  
    1.  輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。  
  
    2.  輸入任何 16 位數的數字中**帳戶號碼**文字方塊。  
  
    3.  選取**SOAP (WS Call)**和**配接器**中**選取傳輸與參數**群組方塊。  
  
    4.  輸入下列 URL 中的**URL**文字方塊中，例如：  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter/CustomerServicePort.asmx`  
  
    5.  型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    6.  型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    7.  按一下**取得我的平衡**。  
  
    8.  回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。  
  
         ![執行配接器版本的用戶端應用程式](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")  
  
4.  在 BTSScnSOSimpleClient.exe 中，依下列方式透過 MQSeries 傳輸傳送要求：  
  
    1.  輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。  
  
    2.  輸入 16 位數數字中的**帳戶號碼**文字方塊。  
  
    3.  選取**MQSeries**中**選取傳輸與參數**群組方塊。  
  
    4.  型別\<*佇列管理員名稱*\>中**佇列管理員**文字方塊。 Qm_<\<*您的電腦名稱*\>是預設值\<*佇列管理員名稱*\>。  
  
    5.  型別`AdapterSOAInputQueue`中**輸入佇列**文字方塊。  
  
    6.  型別`AdapterSOAOutputQueue`中**輸出佇列**文字方塊。  
  
    7.  型別\<*通道定義*\>中**通道定義**方塊。 S_\<*您的電腦名稱*\>/TCP/\<*您的電腦名稱*\>(1414) 是預設值為\< *通道定義*\>。  
  
    8.  型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    9. 型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    10. 按一下**取得我的平衡**。  
  
    11. 回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。  
  
         ![執行配接器版本的用戶端應用程式](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")  
  
##  <a name="step5"></a>使用用戶端應用程式 （內嵌版本） 傳送要求  
  
#### <a name="to-send-requests-using-the-client-application-inline-version"></a>使用用戶端應用程式 (內嵌版本) 傳送要求  
  
1.  開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug，，然後執行下列命令以啟動付款追蹤器模擬器：  
  
     `BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*佇列管理員名稱* `> 5 [<` *通道定義*`>]`  
  
    > [!NOTE]
    >  若不是 MQSeries Server，則通道定義為選擇性。  
  
    > [!NOTE]
    >  若付款追蹤器模擬器已經在執行中，請略過此步驟。  
  
    -   讓付款追蹤器模擬器繼續執行。  
  
2.  在**BizTalk Server 管理主控台**，依序展開**BTSScn.SO.CustomerService**，按一下 **接收位置**，以滑鼠右鍵按一下**Paymenttrackingsystemoutputqueue**在右窗格中，然後按一下**停用**。  
  
    > [!NOTE]
    >  配接器版本和內嵌版本會使用相同的 MQSeries 佇列 LastPaymentsOutputQueue。 若要避免兩個版本之間出現競爭條件，請停用 MQSeries 佇列上配接器版本的接收位置待命。  
  
3.  開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。  
  
4.  在 BTSScnSOSimpleClient.exe 中，使用下列方式透過 SOAP 傳輸傳送要求：  
  
    1.  輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。  
  
    2.  輸入任何 16 位數的數字中**帳戶號碼**文字方塊。  
  
    3.  選取**SOAP (WS Call)**和**內嵌**中**選取傳輸與參數**群組方塊。  
  
    4.  輸入下列 URL 中的**URL**文字方塊中，例如：  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline/CustomerServicePort.asmx`  
  
    5.  型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    6.  型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    7.  按一下**取得我的平衡**。  
  
    8.  回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。  
  
         ![執行內嵌版本的用戶端應用程式](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")  
  
5.  在 BTSScnSOSimpleClient.exe 中，依下列方式透過 MQSeries 傳輸傳送要求：  
  
    1.  輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。  
  
    2.  輸入 16 位數數字中的**帳戶號碼**文字方塊。  
  
    3.  選取**MQSeries**中**選取傳輸與參數**群組方塊。  
  
    4.  型別\<*佇列管理員名稱*\>中**佇列管理員**文字方塊。 Qm_<\<*您的電腦名稱*\>是預設值\<*佇列管理員名稱*\>。  
  
    5.  型別`InlineSOAInputQueue`中**輸入佇列**文字方塊。  
  
    6.  型別`InlineSOAOutputQueue`中**輸出佇列**文字方塊。  
  
    7.  型別\<*通道定義*\>中**通道定義**方塊。 S_\<*您的電腦名稱*\>/TCP/\<*您的電腦名稱*\>(1414) 是預設值為\< *通道定義*\>。  
  
    8.  型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    9. 型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。  
  
    10. 按一下**取得我的平衡**。  
  
    11. 回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。  
  
         ![執行內嵌版本的用戶端應用程式](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")  
  
## <a name="see-also"></a>請參閱  
 [然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md)   
 [How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [服務導向解決方案的開發人員電腦設定](../core/developer-machine-setup-for-the-service-oriented-solution.md)