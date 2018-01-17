---
title: "核准訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, approving
- approving messages
ms.assetid: e6abfef3-aab2-470e-a7a7-a6d091ffba53
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3bdbd4845ddc1dff698274492f33ec69d659188
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="approving-a-message"></a>核准訊息
本章節描述如何核准訊息修復和驗證。  
  
### <a name="to-approve-a-message"></a>核准訊息  
  
1.  在 Internet Explorer 中，開啟 MRSR http://localhost/sites/bassite 您的網站。  
  
2.  在 [首頁] 視窗中，按一下**文件**。  
  
3.  在文件視窗中，在**文件庫**，按一下   **\<*部門名稱*\>_Approver**。  
  
4.  在\<部門名稱\>_Approver 視窗中，按一下 **收件匣**。  
  
5.  在 收件匣 視窗中，指向 訊息的標題、 按一下訊息標題右邊的箭號，然後按一下**編輯在 Microsoft Office InfoPath**。  
  
6.  SWIFT 加速器窗格[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年] 視窗中，按一下 [**錯誤**。 檢閱中顯示任何錯誤**剖析和 XML 驗證錯誤** 方塊中， **BRE 驗證錯誤** 方塊中，而**執行階段錯誤**方塊。  
  
7.  在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 捲動到 錯誤的位置，確認已更正錯誤。 您可以看到原始錯誤是依序按一下**錯誤**目前的角色： 核准窗格中，並在其中一個錯誤窗格中檢視錯誤。 您也可以比較出來和修復版本的訊息，依序按一下**訊息詳細資料**目前的角色： 核准窗格。  
  
8.  若要確定會驗證訊息，**驗證**目前的角色： 核准窗格中，然後按一下 **驗證訊息**。 確認 [結果] 窗格會顯示訊息**訊息無效**。  
  
9. 如果您已對文件中進行之變更的核准[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年] 視窗中，按一下 [**送出**。  
  
    > [!NOTE]
    >  當您按一下**送出**，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]對訊息執行 XML 驗證。 如果驗證不成功，您必須修正驗證錯誤後再繼續。  
  
10. 在 提交訊息 對話方塊中，按一下 **接受**提交核准的訊息以接受變更。 按一下**拒絕**來提交訊息被拒絕的變更。 按一下**取消**取消提交作業，並返回表單。  
  
    > [!NOTE]
    >  如果您接受訊息的變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 BRE 驗證訊息。  
  
    > [!NOTE]
    >  如果您拒絕訊息的修訂，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將訊息傳回至工作流程的第一個階段 （建立或修復），並重設修復工作流程。  
  
11. 在選取的憑證來簽署格式的數位簽章精靈頁面上，選取您想要使用的表單 （建立的憑證，您的核准者） 的憑證。 按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。 按一下 **[下一步]**。  
  
    > [!NOTE]
    >  若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**. 您也可以查看哪些角色已登入的表單先前 （表單可以只由簽署一次每個工作流程的人員），即可**數位簽章**上**工具**功能表。 如果您要新增此角色的另一個簽章，請執行這個動作[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台。  
  
12. 在輸入的註解的數位簽章精靈頁面上，按一下 **完成**。  
  
13. 在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息正確。 按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。 按一下**我已簽署前確認此內容**，然後按一下 **登**。  
  
14. 在 [確認數位簽章] 視窗中，按一下**關閉**。  
  
15. 在 [提交成功] 對話方塊中，按一下**確定**。  
  
16. 關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。  
  
17. 在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，開啟的資料夾，您將設定為接收已傳送的訊息。 請確認該資料夾包含已核准的訊息。 若要確認已修復訊息的文字編輯器中開啟的郵件。