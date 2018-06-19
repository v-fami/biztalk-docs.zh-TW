---
title: 模組 7： 測試有效的一般檔案執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, flat file instance
- tutorial, testing flat file instance
- flat files, testing
ms.assetid: ba8a5d81-41b0-4da7-8c2e-02cf29953af7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 572df71fe479bc26e6b803cdbb95ff7a409c394a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209814"
---
# <a name="module-7-testing-a-valid-flat-file-instance"></a>模組 7： 測試有效的一般檔案執行個體
此模組中，您送出有效的範例 MT103 檔案的一般檔案接收埠建立在先前的實驗室中。 這項工作中測試您在上一個實驗室中建立的接收管線。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]以 XML 格式的輸出寫入輸出資料夾中上一課，您所選取的傳送埠[第 2 課： 加入 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md)。  
  
 起始檔案接收配接器會將 SWIFT 一般格式的檔案複製到 [傳入] 資料夾。 這個動作會導致[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]路由傳送至輸出資料夾的有效 SWIFT XML 檔案。  
  
 在這項工作，您也會提交 MT103 訊息無效。 您可以使用 「 事件解決錯誤。  
  
 此部分包含：  
  
-   [第 1 課： 送出範例一般檔案](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md)  
  
-   [第 2 課： 送出不是有效的 MT103 訊息](../../adapters-and-accelerators/accelerator-swift/lesson-2-submitting-an-mt103-message-that-is-not-valid.md)  
  
-   [第 3 課： 測試 XML 執行個體](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md)