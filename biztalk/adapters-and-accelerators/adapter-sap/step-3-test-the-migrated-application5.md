---
title: "步驟 3： 測試移轉的 Application5 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Receive IDOC)
- migration
ms.assetid: 3ad15069-1556-4c0a-8bfd-86704d40c586
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e49968e4b0b463b1665d0752689a14039c2da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application"></a>步驟 3： 測試已移轉的應用程式
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：**在此步驟中，您會測試已移轉的應用程式接收一般檔案 IDOC 使用 WCF 型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
  
-   將 BizTalk 協調流程中的邏輯連接埠對應至實體連接埠，BizTalk Server 管理主控台中設定的 BizTalk 應用程式。  
  
-   設定 BizTalk 應用程式使用 WCF 自訂接收埠，讓 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1.  啟動 SAP GUI，並連接至 SAP 系統連接 URI 中所指定。  
  
2.  執行 SE37，並叫用傳送 IDOC 至外部系統的 SAP 中的函式模組。 請確定您傳送 IDOC 使用 Wcf-custom 接收埠，會將連接 URI 中指定的相同程式識別碼。  
  
3.  查看輸入 IDOC 的協調流程中指定的檔案位置。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 移轉 SAP 接收 IDOC 的 BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)