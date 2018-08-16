---
title: 第 2 課： 新增 XML 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, XML ports
- XML ports
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63d955b46ca007aea7ea74960e756520a82f43b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005327"
---
# <a name="lesson-2-adding-an-xml-send-port"></a>第 2 課： 新增 XML 傳送埠
您可以使用傳送埠定義您想要傳送的訊息的方式。 在這一課，您可以建立傳送埠，以定義傳送 XML 訊息的方式。  

### <a name="to-add-an-xml-send-port"></a>若要新增 XML 傳送埠  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

2. 在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入**MT103_XML_SendPort**。  

3. 在**傳輸**區段中，如**型別**方塊中，按一下下拉式清單中，並選取**檔案**。  

4. 按一下 **設定**按鈕右邊的 類型 下拉式清單。  

5. 在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  

6. 在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs\Outbound**資料夾，然後再按一下**確定**。  

7. 在 [FILE 傳輸屬性] 對話方塊中，確定 **%MessageID%.xml**中輸入**檔名**方塊，然後再按一下**確定**。  

8. 在傳送埠屬性 對話方塊中，請確認**BizTalkServerApplication**選取**傳送處理常式**中，且**PassThruTransmit**選取**傳送管線** 方塊中。  

9. 在左窗格中，按一下**篩選**，然後執行下列操作：  


   |   使用   |              以進行此動作              |
   |--------------|--------------------------------------|
   | **屬性** |   選取**BTS。ReceivePortName**。    |
   | **[運算子]** |            選取  **==**。            |
   |  **ReplTest1**   | 型別**MT103_FlatFile_ReceivePort**。 |
   |  **群組**   |           選取 **和**。            |


10. 按一下 [下一步] 的屬性列中並執行下列作業：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**|  
    |**[運算子]**|選取  **==**。|  
    |**ReplTest1**|型別**False**有效的訊息。|  

    > [!NOTE]
    >  您將新增 **"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"** 篩選運算式子句，讓傳送埠傳送僅成功剖析及驗證訊息。 不同於接收管線中使用原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解譯器，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解譯器不會擱置失敗 （錯誤） 的訊息，但改為將其發佈到 MessageBox 和標記為失敗，使用 升級的屬性。 A4SWIFT 附加失敗的訊息發佈到 MessageBox 之前收集到的錯誤的 XML 表示法。  
    > 但不包括 「 Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"篩選運算式子句中，您的傳送埠會將傳送所有訊息： 成功或失敗。 如需有關失敗的訊息的訂用帳戶的詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。  

11. 按一下 **套用**，然後按一下**確定**。  

12. 在 BizTalk Server 管理主控台中，在**傳送埠**，以滑鼠右鍵按一下**MT103_XML_SendPort**，然後按一下**啟動**。  

    請繼續進行[模組 6： 部署商務規則](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)。