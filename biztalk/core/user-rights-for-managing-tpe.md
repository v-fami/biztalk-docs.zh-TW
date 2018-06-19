---
title: 管理 TPE 的使用者權限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, Tracking Profile Editor
- Tracking Profile Editor, security
ms.assetid: a0353c4d-2aaa-49ac-8e50-88885962abba
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3319a807b1357201dade0c53d04c26146c2b1e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286926"
---
# <a name="user-rights-for-managing-tpe"></a>管理 TPE 的使用者權限
方案開發人員、系統管理員或 IT/操作人員必須擁有系統管理權限，才能擷取追蹤設定檔，或將追蹤設定檔部署至與組件關聯的資料庫。  
  
> [!IMPORTANT]
>  您無法使用追蹤設定檔編輯器 (TPE) 來定義使用者角色，或是授與或拒絕使用者權限。 您只能在 Microsoft SQL Server 中定義這些使用者角色和相關權限。  
  
 有了 TPE，系統管理員可以：  
  
-   從 BizTalk 管理資料庫擷取與一或多個組件關聯的作用中追蹤設定檔  
  
-   修改追蹤設定檔  
  
-   將新的或修改過的追蹤設定檔套用至 BizTalk 管理資料庫  
  
-   修改先前儲存的追蹤設定檔案 (.btt)  
  
    > [!NOTE]
    >  追蹤設定檔案並非設定檔內容的最終版本。 不過 TPE 還是可以將追蹤檔儲存至檔案，儘管 TPE 主要是用來從 BizTalk Server 和 BAM 資料庫提取設定檔內容，以及將設定檔內容發佈至 BizTalk Server 和 BAM 資料庫。 只要檔案內容符合資料庫中儲存的資訊，您仍可以使用追蹤設定檔案來編輯或更新先前儲存的設定檔。 此外，追蹤設定檔也可以封裝在 BizTalk Server 應用程式封裝內。 含有追蹤設定檔的應用程式封裝會在 MSI 封裝匯入至指定的 BizTalk Server 安裝時，自動叫用 BTTDeploy.exe 以套用追蹤設定檔。  
  
> [!IMPORTANT]
>  在 TPE 工作流程中，通常會假設開發和部署工作是分開的，而負責部署的人員應該會有 .btt 檔案和關聯組件檔案的唯讀存取權。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 工作流程](../core/bam-workflow.md)   
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)