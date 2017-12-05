---
title: "確認訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, verifying
- verifying, messages
ms.assetid: df2b72bb-4dc1-4fdd-8f63-35fc73a12151
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f2fdc186e93bd182b3021a3ef8fc258cee59923
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="verifying-a-message"></a>確認訊息
本章節描述如何確認已修復的訊息。  
  
### <a name="to-verify-a-message"></a>若要確認訊息  
  
1.  在 Internet Explorer 中，開啟 MRSR http://localhost/sites/bassite 您的網站。  
  
2.  在 [首頁] 視窗中，按一下**文件**。  
  
3.  在文件視窗中，在**文件庫**，按一下    **\<*部門名稱*\>_Verifier * *。  
  
4.  在確認視窗中，按一下 **收件匣**。  
  
5.  在 確認收件匣 視窗中，指向 訊息的標題，請按一下訊息標題右邊的箭號，然後按一下**編輯在 Microsoft Office InfoPath**。  
  
6.  在**檔案下載**對話方塊中，按一下 **開啟**。  
  
7.  中的目前角色： RekeyVerify 窗格[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年] 視窗中，按一下 [**錯誤**。 檢閱中顯示任何錯誤**剖析和 XML 驗證錯誤**方塊和**BRE 驗證錯誤**方塊。  
  
8.  在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 捲動到 錯誤的位置，確認已更正錯誤。 您可以看到原始錯誤是依序按一下**錯誤**目前的角色： RekeyVerify 窗格中，以及在其中一個錯誤窗格中檢視錯誤。 您也可以比較出來和修復版本的訊息，依序按一下**訊息詳細資料**目前的角色： RekeyVerify 窗格。  
  
9. 若要確定會驗證訊息，**驗證**目前的角色： RekeyVerify] 窗格中，然後按一下 [**驗證訊息**。  
  
    > [!NOTE]
    >  在目前的角色中的訊息驗證的 [結果] 窗格： RekeyVerify 窗格中會指出您需要重設金鑰的訊息中的所有欄位。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將標示紅色星號 [訊息] 窗格中的這些欄位。  
  
10. 重新鍵入資料，以紅色星號 （表示資料，必須 rekeyed 送出前） 標示為 [訊息] 窗格中的所有欄位至。  
  
    > [!NOTE]
    >  您也可以按一下來重設金鑰訊息欄位中顯示的資料，您需要**訊息詳細資料**目前的角色： RekeyVerify 窗格中，並捲動至欄位的原始訊息。 這是，則為 true，除非發生驗證錯誤中的其中一個在原始訊息中，重設金鑰欄位必須在此情況下修復欄位，當您重設金鑰。  
  
11. 按一下**驗證**中**目前角色： RekeyVerify**  窗格中，然後再按一下**驗證訊息**。 確認 [結果] 窗格會顯示訊息**訊息無效**。  
  
12. 按一下**送出**中[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年視窗。  
  
    > [!NOTE]
    >  當您按一下**送出**，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]對訊息執行 XML 驗證。 如果驗證不成功，您必須修正驗證錯誤後再繼續。  
  
13. 在 提交訊息 對話方塊中，按一下 **接受**提交變更接受已驗證的訊息。 按一下**拒絕**來提交訊息被拒絕的變更。 按一下**取消**取消提交作業，並返回表單。  
  
    > [!NOTE]
    >  如果您接受訊息的變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 BRE 驗證訊息。  
  
    > [!NOTE]
    >  如果您拒絕訊息的修訂，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將訊息傳回至工作流程的第一個階段 （建立或修復），並重設修復工作流程。  
  
14. 在選取的憑證來簽署格式的數位簽章精靈頁面上，選取您想要使用的表單 （憑證驗證器所建立），憑證及 **下一步**。  
  
    > [!NOTE]
    >  若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**. 如果您要新增此角色的另一個簽章，請執行這個動作[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台。  
  
15. 在輸入的註解的數位簽章精靈頁面上，按一下 **完成**。  
  
16. 在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息正確。 按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。 按一下**我已簽署前確認此內容**，然後按一下 **登**。  
  
17. 在 [確認數位簽章] 視窗中，按一下**關閉**。  
  
18. 在 [提交成功] 對話方塊中，按一下**確定**。  
  
19. 關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。  
  
20. 在 MRSR 網站中，按一下 **文件，並列出**。 如果您按下**接受**接受步驟 13 中的變更，請確認\<部門名稱\>_Approve 文件庫包含未修改過的訊息。 如果您已經有開啟的文件與清單 視窗，按一下**重新整理**上**檢視**功能表。 如果您按下**拒絕**拒絕步驟 13 中的變更，確認*\<電腦名稱\>*_Outbox 文件庫包含未修改過的訊息。