---
title: 建立 FRR 傳送埠來傳送至自訂處理常式 |Microsoft Docs
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
ms.openlocfilehash: ed467b149674580b9ed8921a59433c5402a24a0e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013935"
---
# <a name="creating-the-frr-send-ports-for-sending-to-the-custom-handlers"></a>建立 FRR 傳送埠來傳送至自訂處理常式
若要執行 FIN 回應對帳，您需要建立的一連串的傳送埠，其中每個會傳送一則訊息 （原始的訊息或回應） 從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理相互關聯的訊息的自訂處理常式。  

 **摘要**  

 使用下列屬性和元件的 BTS 的值來區分每個建立一系列的傳送埠。在篩選中的作業：  


|        屬性/元件        |                                             設定                                              |
|----------------------------------|--------------------------------------------------------------------------------------------------|
|            傳送埠             |                                       靜態單向連接埠                                        |
|          傳輸類型          |                                               FILE                                               |
| 目的地資料夾 (位址 URI) |                         您想要將訊息傳送至資料夾                          |
|     檔案名稱 (位址 URI)      |                                         %MessageID%.txt                                          |
|          傳送管線           | Microsoft。BizTalk.DefaultPipelines。 PassThruTransmit |
|             篩選              |                                   下表所示                                   |

 BTS 的值來區別不同的訊息的傳送埠。在 傳送埠的篩選器的作業。  

### <a name="to-add-frr-send-ports-for-sending-to-the-custom-handlers"></a>若要新增將傳送至自訂處理常式的 FRR 傳送埠  

1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態一個 waySend 埠**。  

2.  在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入傳送埠，例如 FRRCustomHandlersSendPort 的名稱。  

3.  針對**型別**，選取**檔案**。  

4.  按一下 **設定**。  

5.  在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  

6.  在 [瀏覽資料夾] 對話方塊中，移至您想要傳送訊息的來源資料夾。 按一下 [確定] 。  

    > [!NOTE]
    >  如果此資料夾不存在，您可以使用建立它**建立新資料夾**命令。  

7.  在 **檔名**方塊中，輸入 **%MessageID%.txt**，然後按一下  **確定**。  

    > [!NOTE]
    >  您可以建立不同的資料夾，每種類型的訊息。  

8.  在 傳送埠屬性 對話方塊的 傳送處理常式中，確認**BizTalkServerApplication**已選取。  

9. 針對**傳送管線**，選取**PassThruTransmit**。  

10. 按一下 **篩選器**左的窗格中，然後執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**A4SWIFT_FrrService**。|  
    |**群組**|**和**|  
    |**屬性**|選取**BTS。作業**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|輸入 BTS 的其中一個。下表中的作業值。|  

     針對 BTS。作業中，輸入下列值之一：  

    |訊息類型|BTS。作業值|  
    |------------------|-------------------------|  
    |所有類別 0 到 9 SWIFT FIN 訊息類型|**A4SWIFT_FrrSendMTMsg**|  
    |MQ 系列移動瀏覽/NAN (MQ Series 傳輸層級通知/NAK)|**A4SWIFT_FrrSendTransport**|  
    |MT010 （非傳遞警告）|**A4SWIFT_FrrSend010NDW**|  
    |MT011 （傳遞通知）|**A4SWIFT_FrrSend011Delivered**|  
    |MT012 （寄件者通知）|**A4SWIFT_FrrSend012SenderACK**|  
    |MT015 （DNK 或延遲的 NAK）|**A4SWIFT_FrrSend015DNK**|  
    |MT019 （中止通知）|**A4SWIFT_FrrSend019Abort**|  
    |MTS21_FIN_ACKNAK （FIN 訊息傳送的 L (ACK) 的通知|**A4SWIFT_FrrSendS21ACK**|  
    |MTS21_FIN_ACKNAK （負值通知的傳送 L (NAK) 由 FIN 訊息|**A4SWIFT_FrrSendS21NAK**|  

11. 為類別 0 到 9 SWIFT FIN 訊息未成功傳送，執行下列**篩選器**窗格：  

    > [!NOTE]
    >  **A4SWIFT_FRRFailedReason**應群組在下列的篩選條件中的屬性。  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**A4SWIFT_FrrService**。|  
    |**群組**|**和**|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別 **，則為 True**。|  
    |**群組**|**和**|  
    |**屬性**|選取**BTS。作業**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**A4SWIFT_FrrSendMTMsg**。|  
    |**群組**|**和**|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別 *\<NAKErrorCode\>*，例如"Y01 」。|  
    |**群組**|**Or**|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**TimedOut**。|  
    |**群組**|**Or**|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**TransportError**。|  
    |**群組**|**Or**|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**DelayedNAK**。|  
    |**群組**|**Or**|  
    |**屬性**|選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**AbortMessage**。|  

12. 按一下 **套用**，然後按一下**確定**。  

13. 以滑鼠右鍵按一下傳送埠，然後按一下**啟動**。  

14. 重複步驟 2 到 13，以建立傳送埠所需每種訊息類型。