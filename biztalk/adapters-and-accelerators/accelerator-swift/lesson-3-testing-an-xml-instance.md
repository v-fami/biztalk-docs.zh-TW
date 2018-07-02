---
title: 第 3 課： 測試 XML 執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, XML instances
- XML instances
ms.assetid: 19d7dd18-17dc-4355-a4f1-5c5e6750faf3
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5660ab4e67545b1b98785aedeaeea6e123b6d008
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971895"
---
# <a name="lesson-3-testing-an-xml-instance"></a>第 3 課： 測試 XML 執行個體
在這一課，您可以提交有效的 MT103 訊息檔案的 XML 格式接收在先前的課程中建立的連接埠。 此動作會測試您在前一個模組中建立的傳送管線。 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]以一般檔案的輸出寫入您選取在前一個模組中的傳送埠的輸出資料夾。  
  
 起始檔案接收配接器藉由將 SWIFT XML 格式的檔案複製到輸入資料夾。 此動作會導致系統將有效的 SWIFT 一般檔案複製到輸出資料夾。  
  
### <a name="to-test-an-xml-instance"></a>若要測試 XML 執行個體  
  
1. 在 Windows 檔案總管中，開啟\<*磁碟機*\>: \Labs\Outbound。 請確認此資料夾包含您傳送到此資料夾中的 {GUID}.xml 檔案[第 1 課： 提交範例一般檔案](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md)此模組。  
  
2. 複製 XML 檔案，並將它貼至\<*磁碟機*\>: \Labs\Inbound\XMLFile。 請注意，您所貼上此檔案的時間。  
  
3. 移至\<*磁碟機*\>: \Labs\Outbound。 驗證是否在這個資料夾中，名為 {GUID}.txt 的檔案，以及此檔案修改日期資料行中的時間會對應到您所貼上檔案的時間\<*磁碟機*\>: \Labs\Inbound\XMLFile。  
  
4. 在 記事本 開啟 在 MT103_Sample.txt \<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial。  
  
5. 在 記事本 的另一個執行個體，開啟 {GUID} 中的.txt \<*磁碟機*\>: \Labs\Inbound\XMLFile。  
  
6. 確認 [記事本] 中的兩個檔案包含相同的內容。  
  
   請繼續進行[單元 8： 修復無效的訊息](http://msdn.microsoft.com/fb531b22-ac7a-4620-b395-87aebf56077d)。