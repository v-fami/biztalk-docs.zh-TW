---
title: "第 3 課： 測試 XML 執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, XML instances
- XML instances
ms.assetid: 19d7dd18-17dc-4355-a4f1-5c5e6750faf3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7fb7efbe41711213103224bdbcda11eeda6281
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-testing-an-xml-instance"></a>第 3 課： 測試 XML 執行個體
在這一課，您可以提交有效 MT103，XML 格式檔案中的訊息接收在先前課程所建立的連接埠。 這個動作會測試您在前一個模組中建立的傳送管線。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]以一般檔案中將輸出寫入您選取的前一個模組中的傳送埠的輸出資料夾中。  
  
 起始檔案接收配接器複製到輸入資料夾的 SWIFT XML 格式檔案。 這個動作會導致系統複製到輸出資料夾的有效 SWIFT 一般檔案。  
  
### <a name="to-test-an-xml-instance"></a>若要測試 XML 執行個體  
  
1.  在 Windows 檔案總管 中，開啟\<*磁碟機*>: \Labs\Outbound。 請確認此資料夾包含您傳送至這個資料夾中的 {GUID}.xml 檔案[第 1 課： 送出範例一般檔案](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md)此模組。  
  
2.  複製 XML 檔案，並將它貼入\<*磁碟機*>: \Labs\Inbound\XMLFile。 請注意，您所貼上這個檔案的時間。  
  
3.  移至\<*磁碟機*>: \Labs\Outbound。 請確認沒有在這個資料夾中，稱為 {GUID}.txt 的檔案，而且這個檔案修改日期資料行中的時間，對應至您所貼上檔案的時間\<*磁碟機*>: \Labs\Inbound\XMLFile。  
  
4.  在 [記事本] 開啟中的 MT103_Sample.txt \<*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial。  
  
5.  在 記事本 的另一個執行個體，開啟 {GUID} 中的.txt \<*磁碟機*>: \Labs\Inbound\XMLFile。  
  
6.  請確認 [記事本] 中的兩個檔案都包含相同的內容。  
  
 若要繼續[單元 8： 修復無效的訊息](http://msdn.microsoft.com/en-us/fb531b22-ac7a-4620-b395-87aebf56077d)。