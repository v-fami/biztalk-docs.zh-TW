---
title: 如何顯示管理組件的監視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7c4d2b3-9c01-40f5-b983-bf29a3a5cacc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d561c7b49c47d59f7affccaaee582e26db500c09
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010271"
---
# <a name="how-to-display-monitors-for-a-management-pack"></a>如何顯示管理組件的監視
若要顯示的輸出清單的管理組件的監視和覆寫命令殼層，請使用下列程序。  
  
### <a name="to-display-monitors-for-a-management-pack"></a>若要顯示管理組件的監視  
  
1. 在 管理伺服器中，按一下**程式**，然後按一下  **System Center。**  
  
2. 按一下 **命令殼層**。  
  
3. 在命令殼層中，輸入下列命令：   
   `get-scommanagementpack –DisplayName “DisplayName” | get-scommonitor | export.csv filename`  
  
4. 建立.csv 檔案。 可以在 Microsoft Office Excel 中開啟.csv 檔案。  
  
   > [!NOTE]  
   >  在 Excel 中，您可能需要指定此.csv 檔案為文字檔。  
  
   例如，下列命令會擷取資料的其中一個核心管理組件相關聯的監視：   
   `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-ScomMonitor | export-csv "c:\monitors.csv"`