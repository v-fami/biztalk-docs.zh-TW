---
title: 處理未剖析的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unparsed messages
- messages, unparsed messages
ms.assetid: c6a67ff3-3295-489f-9d5f-fb35b2bf8b19
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b24b7db4013e5e1f8fdb03c1278a19dc070d0e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998663"
---
# <a name="handling-an-unparsed-message"></a>處理未剖析的訊息
本節說明如何處理未剖析的訊息。 不同於無法通過驗證的訊息，您無法修復的訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]無法剖析。 Message Repair 和 New Submission 會顯示訊息和剖析錯誤的本質，並讓您列印訊息，或將它儲存到本機檔案。 然後，您可以警示將訊息傳送至特定的剖析失敗本質的實體。  

### <a name="to-handle-an-unparsed-message"></a>若要處理未剖析的訊息  

1. 在 Internet Explorer 中，開啟 MRSR 網站 http://localhost/sites/bassite 。  

2. 在 [首頁] 視窗中，按一下**文件**。  

3. 在文件視窗中，在**文件庫**，按一下**Unparsed**。  

4. 在未剖析的視窗中，按一下**收件匣**。  

5. 未剖析的收件匣 視窗中，在提供的訊息，未不剖析、 按一下訊息，右邊的箭號，然後按一下**在 Microsoft Office InfoPath 中編輯**。  

6. 在 [SWIFT 加速器] 窗格中，按一下**錯誤**。  

7. XML 驗證錯誤與剖析中 窗格中，會讀取剖析錯誤。  

8. 在剖析的訊息 窗格中，檢閱該訊息。  

   > [!NOTE]
   >  如果您想要在列印訊息時，剖析的訊息 窗格中，於**檔案**功能表上，按一下**列印**。  
   > 
   > [!NOTE]
   >  如果您想要將訊息儲存到本機檔案，在剖析的訊息 窗格中，於**檔案**功能表上，按一下**另存新檔**。 在**另存新檔**對話方塊中，於**將儲存在**下拉式清單中，移至您想要儲存的檔案中，然後再按一下資料夾**確定**。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 將訊息儲存在 XML 格式。  

9. 在剖析的訊息 窗格中，進行必要的變更，，然後按一下**送出**。  

    > [!NOTE]
    >  您無法驗證您修復未剖析的訊息。  

10. 在 提交訊息 對話方塊中，按一下**接受**提交已修復的訊息，以接受變更，按一下**拒絕**拒絕變更，或按一下 **取消**取消送出，並返回表單。  

11. 如果您按下**Accept**或是**拒絕**在步驟 11 中，在數位簽章精靈頁面上，選取您想要用來簽署表單 （您為 repairer 建立憑證，） 的憑證，然後按一下 [**下一步]**。  

    > [!NOTE]
    >  若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.  

    > [!NOTE]
    >  任何執行的任何角色的使用者可以送出他們修復未剖析的訊息。  

12. 在輸入註解 [數位簽章精靈] 頁面上，按一下**完成**。  

13. 在驗證表單的數位簽章精靈頁面，確認您所簽署的訊息正確無誤。 按一下 **檢視憑證**如果您想要確認您使用的正確的簽章。 按一下 **我已登入之前確認此內容**，然後按一下**登**。  

14. 在 [確認數位簽章] 視窗中，按一下**關閉**。  

15. 在 [提交成功] 對話方塊中，按一下**確定**。  

16. 關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。
