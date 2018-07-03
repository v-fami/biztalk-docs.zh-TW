---
title: 步驟 3： 測試已移轉的 Application5 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Receive IDOC)
- migration
ms.assetid: 3ad15069-1556-4c0a-8bfd-86704d40c586
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195b150dcbc3edcd1bfe0a18a17c6fe73cb4f50b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009143"
---
# <a name="step-3-test-the-migrated-application"></a>步驟 3： 測試已移轉的應用程式
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您將測試已移轉的應用程式以接收使用以 WCF 為基礎的一般檔案 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
  
- 將 BizTalk 協調流程中的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠，以設定 BizTalk 應用程式。  
  
- 設定 BizTalk 應用程式使用 WCF 自訂接收埠，讓 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1.  啟動 SAP GUI 中，並連接到您在 連線 URI 中指定的 SAP 系統。  
  
2.  執行 SE37，並叫用 SAP 傳送 IDOC 至外部系統中的函式模組。 請確定您傳送 IDOC 使用 Wcf-custom 接收埠，會將連線 URI 中指定的同一個程式識別碼。  
  
3.  輸入 IDOC 的協調流程中指定的檔案位置的外觀。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4：移轉 SAP 接收 IDOC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)