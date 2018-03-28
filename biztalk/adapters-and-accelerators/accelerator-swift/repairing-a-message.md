---
title: 修復訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages
ms.assetid: 3a61b73b-5433-4249-b580-6194ccb4aebc
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4489e463257f811fe2c71efea49880940751c66a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="repairing-a-message"></a>修復訊息
本章節描述如何修復驗證失敗的訊息。  
  
### <a name="to-repair-a-message"></a>若要修復的訊息  
  
1.  在 Internet Explorer 中，開啟 MRSR 網站，網址http://localhost/sites/bassite。  
  
2.  在 [首頁] 視窗中，按一下**文件**。  
  
3.  在文件視窗中，在**文件庫**，按一下   **\<*部門名稱*\>**_**Repairer**.  
  
4.  在\<*部門名稱*\>_Repair 視窗中，按一下 **收件匣**。  
  
5.  在 收件匣 視窗中，指向 訊息的標題、 按一下訊息標題右邊的箭號，然後按一下**編輯在 Microsoft Office InfoPath**。  
  
6.  SWIFT 加速器窗格[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年 視窗中，確定**錯誤**已選取。 檢閱中顯示任何錯誤**剖析和 XML 驗證錯誤**， **BRE 驗證錯誤**，和**執行階段錯誤**方塊。  
  
7.  在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 捲動至錯誤的位置以及修正錯誤。 如果 XML 驗證錯誤，錯誤都將會以紅色反白顯示。  
  
    > [!NOTE]
    >  BRE 驗證錯誤將不會反白顯示中以紅色[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。 如需 BRE 驗證錯誤的詳細資訊，請參閱[SWIFT 錯誤碼](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md)。  
  
    > [!NOTE]
    >  如果錯誤是發生在伴隨著下拉式清單的欄位，您無法查看造成錯誤的原始值。 欄位會顯示 「 選取 」 而不是原始值。 從下拉式清單中選取適當的值。  
  
8.  若要確定會驗證訊息，**驗證**目前的角色： 修復] 窗格中，，然後按一下 [**驗證訊息**。 確認 [結果] 窗格會顯示**訊息無效**。  
  
9. 在[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年] 視窗中，按一下 [**送出**。  
  
    > [!NOTE]
    >  當您按一下**送出**，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]對訊息執行 XML 驗證。 如果驗證不成功，您必須修正驗證錯誤後再繼續。  
  
10. 在提交訊息 對話方塊中，按一下**接受**要提交修復的訊息，以接受變更，請按一下**拒絕**拒絕變更，或按一下**取消**取消送出，並返回表單。  
  
    > [!NOTE]
    >  如果您接受訊息的變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 BRE 驗證訊息。  
  
    > [!NOTE]
    >  如果您在修復階段中，拒絕的訊息變更[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會將訊息路由至 MessageBox，並張貼至事件檢視器會讀取錯誤 「 無法重設至工作流程中的第一個階段。 」。  
  
11. 如果您按下**接受**或**拒絕**在步驟 10 中，在**數位簽章精靈**頁面上，選取您想要用來簽署格式的憑證 (憑證，您建立 repairer），然後按一下 **下一步**。  
  
    > [!NOTE]
    >  若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.  
  
12. 在輸入註解的數位簽章精靈頁面上，按一下 **完成**。  
  
13. 在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息和簽章正確。 按一下**我已簽署前確認此內容**，然後按一下 **登**。  
  
14. 在 [確認數位簽章] 視窗中，按一下**關閉**。  
  
15. 在 [提交成功] 對話方塊中，按一下**確定**。  
  
16. 關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。  
  
17. 在 MRSR 網站中，按一下 **文件**。 如果您按下**接受**接受步驟 11 中的變更，請確認*\<部門名稱\>*_ReKeyVerify 文件庫包含您修復的訊息。 如果您按下**拒絕**拒絕步驟 11 中的變更，請確認 A4SWIFT_Outbox 文件庫包含未修改過的訊息。