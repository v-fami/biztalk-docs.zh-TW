---
title: 建立 FRR 傳送埠以傳送到自訂處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 036f1f97-17a2-4e02-a85a-a52739a48528
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a6326ae6e82e819d3cdf76ecc4d81e2a377ea65
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966540"
---
# <a name="creating-the-frr-send-ports-for-sending-to-the-custom-handlers"></a>建立 FRR 傳送埠以傳送到自訂處理常式
若要執行 FIN 回應重新調整，您需要建立的一連串的傳送埠，其中每個傳送訊息 （原始訊息或回應） 從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理的相互關聯的訊息的自訂處理常式。  
  
 **摘要**  
  
 建立具有下列屬性和元件，每個的 BTS 的值來區分的一系列的傳送埠。在篩選中的作業：  
  
|屬性/元件|設定|  
|-------------------------|-------------|  
|傳送埠|靜態單向連接埠|  
|傳輸類型|FILE|  
|目的資料夾 (位址 URI)|您想要將訊息傳送至資料夾|  
|檔案名稱 (位址 URI)|%MessageID%.txt|  
|傳送管線|[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].BizTalk.DefaultPipelines。 PassThruTransmit|  
|篩選|下表所示|  
  
 BTS 的值來區分不同的訊息的傳送埠。傳送埠的篩選條件中的作業。  
  
### <a name="to-add-frr-send-ports-for-sending-to-the-custom-handlers"></a>若要加入 FRR 傳送埠以傳送到自訂處理常式  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態一個 waySend 埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入傳送埠，例如 FRRCustomHandlersSendPort 的名稱。  
  
3.  如**類型**，選取**檔案**。  
  
4.  按一下**設定**。  
  
5.  在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  
  
6.  在 [瀏覽資料夾] 對話方塊中，移至您想要從傳送訊息的資料夾。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  如果此資料夾不存在，您可以建立使用**建立新資料夾**命令。  
  
7.  在**檔案名稱**方塊中，輸入 **%MessageID%.txt**，然後按一下 **確定**。  
  
    > [!NOTE]
    >  您可以建立不同的資料夾，每種類型的訊息。  
  
8.  在 傳送埠屬性 對話方塊的 傳送處理常式中，確認**BizTalkServerApplication**已選取。  
  
9. 如**傳送管線**，選取**PassThruTransmit**。  
  
10. 按一下**篩選**左的窗格中，然後執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**A4SWIFT_FrrService**。|  
    |**群組**|**和**|  
    |**屬性**|選取**BTS。作業**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|輸入 BTS 的其中一個。下表中的作業值。|  
  
     針對 BTS。作業中，輸入下列值之一：  
  
    |訊息類型|BTS。作業值|  
    |------------------|-------------------------|  
    |所有類別 0 到 9 SWIFT FIN 訊息類型|**A4SWIFT_FrrSendMTMsg**|  
    |MQ 系列取景位置調整/NAN (MQ Series 傳輸層級 ACK/NAK)|**A4SWIFT_FrrSendTransport**|  
    |MT010 （非傳遞警告）|**A4SWIFT_FrrSend010NDW**|  
    |MT011 （傳遞通知）|**A4SWIFT_FrrSend011Delivered**|  
    |MT012 （寄件者通知）|**A4SWIFT_FrrSend012SenderACK**|  
    |MT015 （DNK 或延遲的 NAK）|**A4SWIFT_FrrSend015DNK**|  
    |MT019 （中止通知）|**A4SWIFT_FrrSend019Abort**|  
    |MTS21_FIN_ACKNAK 傳送 LT (ACK) 的 FIN 訊息 （通知|**A4SWIFT_FrrSendS21ACK**|  
    |MTS21_FIN_ACKNAK （負值通知的傳送 LT (NAK) 由 FIN 訊息|**A4SWIFT_FrrSendS21NAK**|  
  
11. 針對類別 0 到 9 SWIFT FIN 訊息無法順利傳送，執行下列動作**篩選**窗格：  
  
    > [!NOTE]
    >  **A4SWIFT_FRRFailedReason**應分組在下列的篩選條件中的屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**A4SWIFT_FrrService**。|  
    |**群組**|**和**|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**True**。|  
    |**群組**|**和**|  
    |**屬性**|選取**BTS。作業**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**A4SWIFT_FrrSendMTMsg**。|  
    |**群組**|**和**|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別 *\<NAKErrorCode\>*，例如"Y01"。|  
    |**群組**|**Or**|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**TimedOut**。|  
    |**群組**|**Or**|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**TransportError**。|  
    |**群組**|**Or**|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**DelayedNAK**。|  
    |**群組**|**Or**|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**AbortMessage**。|  
  
12. 按一下**套用**，然後按一下 **確定**。  
  
13. 傳送埠，以滑鼠右鍵按一下，然後按一下 **啟動**。  
  
14. 重複步驟 2 到 13，建立傳送埠所需的每個訊息類型。