---
title: 步驟 3： 測試已移轉的應用程式 2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Send IDOC)
- migration
ms.assetid: 8dc0d127-71ce-4668-a3bf-c893a8f6848d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc49906e58e549a8ed9c90446b011dc3b51e0a45
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017814"
---
# <a name="step-3-test-the-migrated-application"></a>步驟 3： 測試已移轉的應用程式
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您將測試已移轉的應用程式傳送使用以 WCF 為基礎的一般檔案 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
  
- 將 BizTalk 協調流程中的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠，以設定 BizTalk 應用程式。  
  
- 設定要用於 wcf-custom 傳送埠以 WCF 為基礎的 BizTalk 應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1.  從 [SendIDOC_Migration] 資料夾中，複製 BOMDOC.txt 檔案。 這是要傳送至 SAP 系統的一般檔案 IDOC。  
  
2.  貼上的資料夾對應至檔案，一般檔案 IDOC 接收位置。  
  
3.  協調流程會取用該檔案，並傳送 IDOC 至 SAP 系統。 確認 事件檢視器中是否有任何錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3：移轉 SAP 傳送 IDOC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)