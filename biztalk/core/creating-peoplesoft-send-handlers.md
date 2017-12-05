---
title: "建立 PeopleSoft 配接器傳送成品 |Microsoft 文件"
description: "建立傳送埠、 傳送的傳輸屬性，並更新將訊息傳送至 BizTalk Server 中使用 PeopleSoft Enterprise 配接器的 PeopleSoft 的同時呼叫數目上限"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce67da59-26a6-44a2-929c-ed3acb21d407
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc559f4e3c25560540a171b3f47ff25e6f34e89
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-peoplesoft-send-artifacts"></a>建立 PeopleSoft 傳送成品
Microsoft BizTalk Adapter for PeopleSoft Enterprise 會存取 PeopleSoft 並探索可用的元件，或是處理 SOAP 要求。 本主題說明如何在使用 PeopleSoft 配接器的 BizTalk Server 管理 中建立的傳送成品。


## <a name="create-the-send-port"></a>建立傳送埠

1.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**，執行下列動作：  
  
    1.  輸入傳送埠的名稱。 例如，輸入`SSOSendToPeopleSoft`。  
  
    2.  從**類型**下拉式清單中，選取**PeopleSoft**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    5.  從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
    6.  選取**設定**以設定傳送埠。  
  
4.  在**PeopleSoft 傳輸屬性**，執行下列動作：  
  
    1.  展開**配接器必要屬性**，並輸入**應用程式伺服器路徑**， **JAVA_HOME**，**使用者名**， **密碼**，以及 Jar 檔案，以連接至 Peoplesoft 系統。  
  
         您不需要設定登入資訊。  
  
    2.  在此清單中，選取您建立用來代表 PeopleSoft 系統的 SSO 分支機構應用程式。  
  
    3.  如**使用 SSO**，選取**是**。  
  
    4.  選取 [確定]。  
  
5.  選取 [確定]。

## <a name="set-the-transport-properties"></a>設定傳輸屬性
PeopleSoft 傳輸屬性用於設計和執行階段。 在**傳輸屬性**對話方塊中，您設定的連接和認證參數特定伺服器系統和您嘗試存取的物件。  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
1.  展開 [配接器必要屬性]，並填入連線至 PeopleSoft 伺服器的所有必要資訊。  
  
     您必須設定組態參數，Microsoft BizTalk Adapter for PeopleSoft Enterprise 才能連線至 PeopleSoft Enterprise。 此資料區分大小寫。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |`Application Server Path`|字串，表示執行 PeopleSoft Application Server 的電腦和接聽的連接埠。 PeopleSoft 8 應用程式的 URL 路徑的語法是 / / < 電腦名稱 >:\<連接埠\>。 詢問您的 PeopleSoft 系統管理員以\<連接埠\>值。 \<連接埠\>值是 JOLT 通訊協定接聽程式通訊埠，不應用程式伺服器連接埠。 預設 JOLT 連接埠為 9000。|  
    |`JAVA_HOME`|設定 JAVA_HOME 變數以指向 JDK 安裝，例如： **C:\j2sdk1.4.2_08**。|  
    |`Password`|如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。<br /><br /> 字串，表示使用者用來登入 PeopleSoft 系統的密碼。 字元不會顯示出來，而是以星號 (*) 表示。|  
    |`PeopleSoft 8.x Jar Files`|若要使用 Ccmponent 介面 (僅限 PeopleSoft 8)，您必須更新 CLASSPATH 來包含 PeopleSoft 元件介面 jar 檔案。 例如： **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**。|  
    |`User Name`|如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。<br /><br /> 字串，表示登入 PeopleSoft 系統所需的使用者名稱。|  
  
2.  輸入**其他參數**時使用日期做為索引鍵的值; 它有不同的格式。 YYYY-MM-DD 是預設格式。  
  
3.  輸入**並行控制**值中代表的呼叫，例如 200，**同時呼叫數目上限**如有必要。  
  
     **同時呼叫數目上限**參數啟動的多載保護，如果後端伺服器無法處理的資料量。 同時呼叫是指配接器尚未回覆的要求。 設定**同時呼叫數目上限**在輸送量超過後端處理能力。  
  
     此欄位 的預設值為 -1，表示不會提供保護 。  
  
     如果 BizTalk Server 提交要求至傳輸配接器的並行連線數目呼叫等於或超過設定的值**同時呼叫數目上限**、 送出要求會儲存，直到同時呼叫數目的執行緒若要減少設定值以下。  

## <a name="update-max-concurrent-calls"></a>更新最大並行呼叫

`Max Concurrent Calls` 參數是一項可讓您最佳化組態的功能。 您可以在輸送量超過後端處理能力的情況下使用這個參數。 您可以將參數新增到中的配接器**傳送埠傳輸屬性**對話方塊，即可啟動訊息多載保護。 預設值為 -1，表示呼叫沒有上限。  
  
當 BizTalk Server 提交訊息給傳輸配接器時，它會先從配接器接收批次，然後在該批次上叫用 `TransmitMessage()` 來傳輸每個訊息。 完成傳輸時，BizTalk Server 會在批次上叫用 `Done()`，這時配接器就會開始將訊息傳輸至後端。 如果 BizTalk Server 在叫用 `Done` 之前會取得多個批次，`Done` 命令可能就永遠不會發生。 藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。 此參數的變更會立刻生效。 BizTalk Server 必須擷取 SQL 資料庫中儲存的配接器組態變更。  
  
### <a name="change-the-max-concurrent-calls-parameter"></a>變更同時呼叫數目上限參數  
  
1.  在**傳送埠傳輸屬性**對話方塊方塊中，輸入**連接**值。  
  
     預設值為 40 個工作階段。 如果您使用較小的值，則可能會遇到執行階段效能降低的情形。 使用較大的值也是一樣，因為較大的值會超出伺服器的能力，而造成執行階段錯誤。  
  
2.  選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。  
  
     例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。  
  
     **重新整理代理程式**參數會重新整理瀏覽與執行階段代理程式。 runtimeagent.exe 會在一分鐘之後或是下一次呼叫 Send 時更新。  
  
3.  提供認證以存取 PeopleSoft 系統。  
  
     您可以透過兩種方式來存取系統：  
  
    -   登入認證 (傳輸屬性登入參數)  
  
    -   單一登入 (SSO)  
  
4.  選取**是**如**使用 SSO**使用單一登入。  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[安全配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)。 
  
5.  在清單中選取分支機構應用程式。  
  
     由企業單一登入工具所建立的分支機構應用程式，代表像是 PeopleSoft 的應用程式。 Microsoft BizTalk Adapter for PeopleSoft Enterprise 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。 這些認證就是啟動 BizTalk 專案之使用者 (應用程式使用者) 的認證。  
  
    > [!NOTE]
    >  如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications2.md)，或 Microsoft BizTalk Server 線上說明。  
  
6.  提供所有必要的資訊，以採用連線資訊之後, 按一下**套用**，然後按一下 **確定**。  
  
     您必須設定連線參數，讓 BizTalk Adapter for PeopleSoft Enterprise 能夠存取 PeopleSoft。  
  

## <a name="next"></a>下一個
  
[PeopleSoft 結構描述匯入至 BizTalk Server 專案](../core/importing-peoplesoft-schemas-into-biztalk-server-projects.md)  
[從 PeopleSoft 接收](../core/receiving-from-peoplesoft.md)