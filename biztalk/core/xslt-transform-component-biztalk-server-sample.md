---
title: XSLT 轉換元件 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
- XSLT, examples
- examples, XSLT
ms.assetid: 9152e897-4db9-4924-b37e-fd9e908dbef1
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1879cb4d748e974454f929bde2018c24b5d276f2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974924"
---
# <a name="xslt-transform-component-biztalk-server-sample"></a>XSLT 轉換元件 (BizTalk Server 範例)
「XSLT 轉換元件」範例示範如何使用 XSLT 撰寫自訂管線元件以轉換 XML 訊息。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 該範例完成轉換的步驟如下：  
  
1.  從資料夾擷取 XML 文件。  
  
2.  管線使用 Transform.xsl 將 XML 文件轉換為 HTML 電子郵件內文。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Pipelines\XslTransformComponent\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|C# 組件檔案。|  
|Cleanup.bat|範例清除檔。|  
|Confirmation.xsd|範例結構描述檔案。|  
|DocInstance.xml|用來轉換的範例 .xml 檔案。|  
|SendHtmlMessage.btproj|BizTalk 專案。|  
|Setup.bat|組態批次檔。|  
|Xml2HtmlSendPipeline.btp|BizTalk Server 管線檔。|  
|XslTransform.csproj|C# 專案。|  
|XslTransformComponent.sln|範例解決方案檔。|  
|XslTransformComponentBinding.XML|XML 繫結檔案。|  
|XslTransformer.cs|C# 原始程式碼。|  
|Transform.xsl|用來轉換 DocInstance.xml 的 XSLT 檔案。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序，建置和初始化「XSLT 轉換元件」範例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，將目錄變更 (**cd)** 至下列資料夾：  
  
     *\<範例路徑\>* \Pipelines\XslTransformComponent  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   建立範例中所用之輸入 (\In) 和輸出 (\Out) 資料夾。  
  
    -   產生新的金鑰檔案。  
  
    -   建置和部署「XSLT 轉換元件」管線。  
  
    -   若要建置的管線元件會將複製\<安裝路徑\>\Pipeline Components 資料夾。  
  
    -   建立傳送埠和接收埠。  
  
    > [!NOTE]
    >  在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。  
  
    > [!NOTE]
    >  若要復原 Setup.bat 所產生的變更，您必須先從 BizTalk Server 管理 MMC 主控台停止並重新啟動該主控件執行個體。 接著，執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序，執行「XSLT 轉換元件」範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  將 DocInstance.xml 複製至 \In 資料夾。  
  
2.  檢查 \Out 資料夾中的結果 (輸出檔名為 guid.htm)。  
  
## <a name="configuring-this-sample-using-smtp"></a>使用 SMTP 設定此範例  
 請使用下列程序，將「XSLT 轉換元件」範例設定為與 SMTP 伺服器搭配使用。  
  
#### <a name="to-configure-this-sample-using-smtp"></a>若要使用 SMTP 設定此範例  
  
1.  將「XSLT 轉換元件」傳送埠重新設定為使用 SMTP 傳輸類型。  
  
2.  將位址 (URL) 參數變更為符合您的 SMTP 組態以設定 SMTP 設定。  
  
## <a name="running-this-sample-with-output-to-an-smtp-port"></a>執行此範例並輸出至 SMTP 連接埠  
 請使用下列程序，執行「XSLT 轉換元件」範例並輸出至 SMTP 連接埠。  
  
#### <a name="to-run-this-sample-with-output-to-an-smtp-port"></a>若要執行此範例並輸出至 SMTP 連接埠  
  
1.  將 DocInstance.xml 複製至 \In 資料夾。  
  
2.  檢查 SMTP 設定之傳送目標接收者的郵件用戶端中的結果。  
  
## <a name="see-also"></a>請參閱  
 [管線 (BizTalk Server Samples 資料夾)](../core/pipelines-biztalk-server-samples-folder.md)