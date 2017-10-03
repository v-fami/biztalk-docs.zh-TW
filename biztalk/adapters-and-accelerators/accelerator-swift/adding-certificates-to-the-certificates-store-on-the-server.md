---
title: "將憑證加入至伺服器的憑證存放區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, adding to certificates store
- certificates store
ms.assetid: 075cfae8-dce7-46f7-9539-796f03229ea2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94661568108e5a1cc05140a97c933fb8d00e3c67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-certificates-to-the-certificates-store-on-the-server"></a>將憑證新增到伺服器的憑證存放區
使用下列步驟，將憑證加入至伺服器電腦上的憑證 （本機電腦） 存放區的 [其他人] 資料夾。  
  
### <a name="to-add-certificates-to-the-certificate-store"></a>將憑證加入至憑證存放區  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BizTalk Accelerator for SWIFT 管理主控台**。  
  
    > [!NOTE]
    >  如果您仍然可以從上一個程序 （新增憑證至用戶端的憑證存放區），您可以將它用於此程序開啟 MMC 視窗。  
  
2.  在 [系統管理主控台] 視窗中，依序展開**憑證 （本機電腦）**資料夾，然後展開**其他人**。  
  
3.  以滑鼠右鍵按一下**憑證**，指向 **所有工作**，然後按一下 **匯入**。  
  
4.  在歡迎使用 憑證匯入精靈 頁面中，按一下 **下一步**。  
  
5.  在要匯入] 頁面的檔案，按一下 [**瀏覽**。  
  
6.  在開啟的對話方塊中，移至您的憑證，選取的儲存位置的檔案位置**所有檔案**如**檔案類型**，選取您想要匯入，然後按一下 憑證**開啟**。  
  
7.  在要匯入] 頁面的檔案，按一下 [**下一步**。  
  
8.  在憑證存放區 頁面上，確認**將所有憑證都放入以下的存放區**已選取，確認**其他人**會顯示在**憑證存放區**方塊，然後再按一下**下一步**。  
  
9. 在 完成憑證匯入精靈 頁面上，按一下 **完成**。  
  
10. 在表示成功的匯入憑證匯入精靈 對話方塊中，按一下**確定**。  
  
11. 重複步驟 3 到 10，您會使用訊息修復和新送出的所有其他憑證。