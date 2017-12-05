---
title: "透過 AS2 的訊息設定靜態傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2708d6a9-b105-42d3-abe3-7085b39da55a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 068b7d8295710157af7a8a7358768e85e006beb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-a-static-send-port-for-messages-over-as2"></a>為透過 AS2 的訊息設定靜態傳送埠
本主題將說明如何設定讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 透過靜態傳送埠傳送 AS2 訊息。 這項設定包括建立靜態傳送埠和設定協議。 如有需要，您還會設定傳送埠使用的加密憑證。  
  
> [!NOTE]
>  您可以設定動態傳送埠傳送 AS2 訊息，而不使用靜態傳送埠。 如需詳細資訊，請參閱[設定動態傳送埠的訊息，透過 AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)。  
  
 若要傳送含有 EDI 或非 EDI 訊息或 EDI 通知的 AS2 訊息，請建立含下列組態的請求回應 HTTP 傳送埠：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|-靜態請求回應 (如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)<br /><br /> -靜態單向傳送埠 (如果在 要求 MDN**通知 (Mdn)**清除頁面的單向協議索引標籤)|  
|**傳送埠屬性： 一般**|傳輸類型|HTTP<br /><br /> 注意：<br /><br /> 只有 HTTP 配接器能夠用於傳輸 EDIINT/AS2 編碼訊息。 這種傳輸無法搭配 HTTP 配接器以外的配接器運作。|  
|**傳送埠屬性： 一般**|傳送處理常式|BizTalkServerApplication|  
|**傳送埠屬性： 一般**|傳送管線|-AS2EdiSend （用於 EDI 編碼訊息）<br /><br /> -AS2Send （用於非 EDI 訊息）|  
|**傳送埠屬性： 一般**|接收處理常式<br /><br /> (如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)|BizTalkServerApplication|  
|**傳送埠屬性： 一般**|接收管線<br /><br /> (如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)|AS2Receive|  
|**HTTP 傳輸屬性**|目的地 URL|\<目的地 URL 字串\>|  
|**HTTP 傳輸屬性**|啟用區塊編碼|已清除|  
|**傳送埠屬性： 篩選**|屬性|BTS.MessageType<br /><br /> 注意：<br /><br /> 您可以使用各種不同的篩選條件運算式，包括使用 BTS.ReceivePortName。<br /><br /> 注意：<br /><br /> 針對非 EDI 訊息，您將需要篩選不同的屬性|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>`（適用於 EDI 訊息）<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root`(對於 X12 通知)<br /><br /> -                   `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root`（適用於 EDIFACT 通知）|  
|**傳送埠屬性： 憑證**|一般名稱和指紋|如果真對外寄 AS2 訊息使用加密憑證，請輸入憑證名稱和指紋。|  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-biztalk-server-to-send-as2-messages-over-a-static-send-port"></a>設定 BizTalk Server 透過靜態傳送埠傳送 AS2 訊息  
  
1.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立包含上述組態的靜態單向或請求回應傳送埠。  
  
2.  在 [傳送埠] 清單上**傳送埠**頁面的單向協議索引標籤中**協議屬性**對話方塊方塊中，輸入靜態傳送埠的名稱。  
  
    > [!NOTE]
    >  設定傳送埠可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 針對輸出 AS2 訊息執行協議解析。  
  
3.  中**識別碼**單向協議索引標籤的頁面**協議屬性**對話方塊方塊中，設定 [AS2-屬性到目的地，然後視需要在設定其他協議屬性不同頁面**協議屬性**] 對話方塊。  
  
## <a name="functionality"></a>功能  
 傳送埠和管線會執行下列操作，透過 AS2 傳送同步 EDI 或非 EDI 訊息或通知，以及處理傳回的 MDN：  
  
-   如果要傳送 EDI 訊息，請挑選 EDI 訊息，方法是透過篩選在 `BTS.MessageType` 命名空間中設為訊息結構描述 (例如，864 訊息為 X12_00401_864) 的 `http://schemas.microsoft.com/BizTalk/EDI/X12/2006` 屬性。  
  
-   如果要傳送 EDI 通知，請挑選通知，方法是透過篩選設為下列其中一個控制結構描述的 `BTS.MessageType` 屬性：  
  
    -   997 通知為 `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root`  
  
    -   TA1 通知為 `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root`  
  
    -   CONTRL 通知為 `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root`  
  
-   如果要傳送非 EDI 訊息，則會使用另一個篩選條件挑選訊息。  
  
-   建置 AS2 訊息。 如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
-   傳送訊息或通知至傳送埠的目的地 URL。  
  
-   接收訊息或通知的 MDN 回應 (如果已啟用)。 如需此程序的詳細資訊，請參閱[處理內送 MDN](../core/processing-an-incoming-mdn.md)。  
  
## <a name="see-also"></a>請參閱  
 [設定 AS2 方案的連接埠](../core/configuring-ports-for-an-as2-solution.md)   
 [產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)   
 [處理內送 MDN](../core/processing-an-incoming-mdn.md)