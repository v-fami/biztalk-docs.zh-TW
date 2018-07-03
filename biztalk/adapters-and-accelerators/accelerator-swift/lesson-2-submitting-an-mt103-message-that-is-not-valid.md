---
title: 課程 2： 提交無效的 MT103 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, invalid messages
- submitting, invalid messages
- submitting, MT103 messages
- MT103 messages
- messages, MT103 messages
ms.assetid: 4b070ae1-c400-421a-b2f6-b7b1f22c0e41
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cb8f0539f3a832e3b54a6fa45b300558a8e39a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014879"
---
# <a name="lesson-2-submitting-an-mt103-message-that-is-not-valid"></a>課程 2： 提交無效的 MT103 訊息
在這一課，您送出無效的 MT103 訊息，然後您疑難排解使用您的系統工具產生的錯誤。  
  
### <a name="to-submit-an-mt103-message-that-is-not-valid"></a>送出無效的 MT103 訊息  
  
1. 將檔案 MT103_Invalid_Sample.txt 複製從\<*磁碟機：*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial 來\<*磁碟機*\>: \Labs\Inbound\FlatFile 資料夾。 請注意，您將檔案拖放到資料夾的時間。  
  
2. 開啟\<*磁碟機：*\>\Labs\Outbound 以確認沒有 MT103_Invalid_Sample.txt 對應的 XML 檔案的資料夾中。 （對應至有效的 MT103_Sample.txt 訊息的 XML 檔案仍應該為該資料夾中）。  
  
3. 在 記事本 開啟 檔案 MT103_Invalid_Sample.txt 中\<*磁碟機：*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial。  
  
4. 開始**BizTalk Server 管理**。  
  
5. 在 BizTalk Server 管理主控台中，展開**事件檢視器 （本機）**，然後按一下**應用程式**。  
  
6. 尋找具有來源 BizTalk accelerator for SWIFT 和卸除到無效的訊息時，對應於一次的錯誤項目\<*磁碟機*\>: \Labs\Inbound\FlatFile 資料夾。 按兩下該錯誤項目。  
  
7. 在 事件內容 對話方塊中的 錯誤，確認 描述 窗格中失敗的訊息已發佈至 MessageBox，SWIFT 解譯器就會標示**A4SWIFT_Failed**作為 **，則為 True**。 關閉 [事件內容] 對話方塊。  
  
8. 在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**，然後展開**BizTalk 群組**。 在 **檢視**功能表上，按一下**群組中樞頁面**。  
  
9. 在**群組概觀**窗格，請在**分組已擱置服務執行個體**窗格中，按一下 **依應用程式分組**。  
  
10. 在 **預覽選取的查詢結果**窗格中，按兩下項目**MT103_FlatFile_ReceivePort**。  
  
11. 在 服務詳細資料 對話方塊中，按一下**訊息** 索引標籤。按兩下服務名稱的項目**MT103_FlatFile_ReceivePort**。  
  
12. 在 [訊息詳細資料] 對話方塊中，按一下**主體**的左窗格中。  
  
13. 確認 [訊息詳細資料] 對話方塊中的 [主體] 窗格中顯示的訊息對應至您在 「 記事本 」 中開啟 MT103_Invalid_Sample.txt。  
  
    請繼續進行[第 3 課： 測試 XML 執行個體](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md)。