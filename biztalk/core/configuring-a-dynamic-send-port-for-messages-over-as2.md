---
title: "透過 AS2 的訊息設定動態傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246d64e8-70ca-48f4-8b72-d43b0964dbb4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de6df553a3f03e9d2e60b78de9877ad6113b04e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-dynamic-send-port-for-messages-over-as2"></a>為透過 AS2 的訊息設定動態傳送埠
本主題將說明如何設定讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 透過動態傳送埠傳送 AS2 訊息。 這項設定包括建立動態傳送埠，以及設定後端應用程式以設定適當的內容屬性。 在建立動態傳送埠以傳送 AS2 訊息時，您必須升級部分屬性，傳送埠才能運作。 如需詳細資訊，請參閱[設定 BizTalk Server 傳送 AS2 訊息透過動態傳送埠](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md#BKMK_Proc)下方。  
  
 動態傳送埠可以讓您將訊息傳送給多個合作對象，而不用將合作對象組態寫入程式碼。 透過內容屬性，動態地決定傳送訊息所使用的協議與目的地。 您不需要為每個個別的客戶建立靜態傳送埠。  
  
 若要傳送具有 EDI 或非 EDI 訊息或 EDI 通知的 AS2 訊息，請使用下列組態建立動態回應 HTTP 傳送埠：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|-動態請求回應 (如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)<br /><br /> -動態單向傳送埠 (如果在 要求 MDN**通知 (Mdn)**清除頁面的單向協議索引標籤)|  
|**傳送埠屬性： 一般**|傳送管線|-AS2EdiSend （用於 EDI 編碼訊息）<br /><br /> -AS2Send （用於非 EDI 訊息）|  
|**傳送埠屬性： 一般**|接收管線<br /><br /> (如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)|AS2Receive (用於動態請求回應傳送埠)|  
|**傳送埠屬性： 篩選**|屬性|BTS.MessageType|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>`（適用於 EDI 訊息）<br /><br /> - `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root`(對於 X12 通知)<br /><br /> - `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root`（適用於 EDIFACT 通知）|  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
##  <a name="BKMK_Proc"></a>若要設定 BizTalk Server 傳送 AS2 訊息透過動態傳送埠  
  
1.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，使用上述組態，建立動態單向傳送埠 (如果未要求 MDN) 或動態請求回應傳送埠 (如果有要求 MDN)。  
  
2.  對於適用這個訊息的協議，設定必要的 AS2 與 EDI 屬性。  
  
3.  升級訊息內容的下列屬性：  
  
    -   `BTS.MessageType`  
  
    -   `EdiIntAS.MessageID`  
  
4.  在後端應用程式加入功能，以寫入下列訊息內容屬性，並設定為適當值：  
  
    -   `EdiIntAS.AS2To`  
  
    -   `BTS.OutboundTransportLocation`  
  
    -   `HTTP.EnableChunkedEncoding`  
  
    -   `BTS.EncryptionCert`  
  
    > [!NOTE]
    >  `AS2To` 內容屬性與 `OutboundTransportLocation` 內容屬性必須寫入訊息內容中，動態傳送埠才能正常運作。 在處理外寄訊息時，連接埠需要有 `AS2To` 屬性才能決定要使用的協議，而傳送埠需要有 `OutboundTransportLocation` 屬性才能決定訊息目的地。 如需詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
## <a name="functionality"></a>功能  
 動態傳送埠和管線會執行下列操作，透過 AS2 傳送同步 EDI 或非 EDI 訊息或通知，以及處理傳回的 MDN：  
  
-   如果要傳送 EDI 訊息，請挑選 EDI 訊息，方法是透過篩選在 `BTS.MessageType` 中設為訊息結構描述 (例如，864 訊息為 X12_00401_864) 的 `http://schemas.microsoft.com/BizTalk/EDI/X12/2006 namespace` 屬性。  
  
-   如果要傳送 EDI 通知，請挑選通知，方法是透過篩選設為下列其中一個控制結構描述的 `BTS.MessageType` 屬性：  
  
    -   997 通知為 `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root`  
  
    -   TA1 通知為 `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root`  
  
    -   CONTRL 通知為 `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root`  
  
-   如果要傳送非 EDI 訊息，則使用適當的篩選條件挑選訊息。  
  
-   建置 AS2 訊息。 如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會由 URL 的格式 (例如 http、smtp 以及 ftp 等) 來決定動態傳送埠所使用的傳輸類型。  
  
-   路由傳送訊息或通知至傳送埠的目的地 URL。  
  
-   接收訊息或通知的 MDN 回應 (在有啟用且為請求-回應傳送埠的情況下)。 如需此程序的詳細資訊，請參閱[處理內送 MDN](../core/processing-an-incoming-mdn.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 方案的連接埠](../core/configuring-ports-for-an-as2-solution.md)