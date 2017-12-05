---
title: "第 2 課： 加入 XML 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, XML ports
- XML ports
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23d8aac412bf81492793eec2f4936d84b54fda0d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-2-adding-an-xml-send-port"></a>第 2 課： 加入 XML 傳送埠
您可以使用傳送埠定義您想要傳送的訊息的方式。 在這一課，您可以建立傳送埠，以便定義傳送 XML 訊息的方式。  
  
### <a name="to-add-an-xml-send-port"></a>若要加入 XML 傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**MT103_XML_SendPort**。  
  
3.  在**傳輸** 區段中，針對**類型**方塊中，按一下下拉式清單，並選取**檔案**。  
  
4.  按一下**設定**按鈕右邊的 [類型] 下拉式清單。  
  
5.  在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  
  
6.  在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs\Outbound**資料夾，然後再按一下**確定**。  
  
7.  在 [FILE 傳輸屬性] 對話方塊中，確定**%MessageID%.xml**輸入**檔案名稱**方塊，然後再按一下**確定**。  
  
8.  在 [傳送埠屬性] 對話方塊中，確定**[biztalkserverapplication]**選取**傳送處理常式**中，且**PassThruTransmit**選取**傳送管線**方塊。  
  
9. 在左窗格中，按一下 **篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。ReceivePortName**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**MT103_FlatFile_ReceivePort**。|  
    |**群組**|選取**和**。|  
  
10. 按一下 下一步屬性列內部，執行下列：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**False**有效的訊息。|  
  
    > [!NOTE]
    >  您將加入**"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"**篩選運算式子句，讓傳送埠傳送僅成功剖析及驗證訊息。 不同於接收管線中使用原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解譯[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解譯器不會擱置失敗 （錯誤） 的訊息，但改為將其發佈至 MessageBox 和標記為失敗，將使用升級的屬性。 A4SWIFT 附加失敗的訊息發佈到 MessageBox 之前收集到的錯誤的 XML 表示法。  
    > 不包括"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"篩選運算式子句中，您的傳送埠會將傳送所有訊息： 成功或失敗。 如需失敗的訊息訂閱的詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。  
  
11. 按一下**套用**，然後按一下 **確定**。  
  
12. 在 BizTalk Server 管理主控台中，在**傳送埠**，以滑鼠右鍵按一下**MT103_XML_SendPort**，然後按一下 **啟動**。  
  
 若要繼續[模組 6： 部署商務規則](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)。