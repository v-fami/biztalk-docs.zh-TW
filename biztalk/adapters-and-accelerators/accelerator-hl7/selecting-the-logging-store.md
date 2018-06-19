---
title: 選取記錄存放區 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 6ba64c59-3a15-4c10-b44f-18e0e432c6d3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0518b536db16d641b77a61cfeb4851990a7bca0a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960732"
---
# <a name="selecting-the-logging-store"></a>選取記錄存放區
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]選項，例如選取多種不同的記錄存放區中，為您提供[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]Management Instrumentation (WMI) [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，和[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件記錄檔。  
  
 您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管來設定記錄存放區。  
  
 使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管，並選取的記錄存放區。  
  
### <a name="to-open-btahl7-configuration-explorer"></a>若要開啟 BTAHL7 組態總管  
  
-   按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
### <a name="to-select-the--logging-store"></a>若要選取的記錄存放區  
  
1.  在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管上**通用設定**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**WMI**|如果您想要產生 BTAHL7 WMI 通知，請選取此選項。|  
    |**SQL**|選取此選項，如果您想要使用[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]做為您的記錄存放區。 **注意：** BTAHL7 會自動建立所需的記錄，如果它們尚不存在的資料表。|  
    |**[SQL Server]**|型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]名稱。 這是必要的當您選取**SQL**選項。 允許的長度上限為 64 個字元。<br /><br /> 預設的伺服器和資料庫名稱是已設定的 BTAHL7 資料庫。|  
    |**資料庫名稱**|型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫名稱。 這是必要的當您選取**SQL**選項。 最大允許的長度為 128 個字元。|  
    |**事件記錄檔**|選取此選項，如果您想要使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]做為您的記錄存放區的事件記錄檔。 您使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器來檢視事件訊息。|  
  
2.  按一下 **[儲存]**。  
  
    > [!NOTE]
    >  地區設定的記錄所記錄的事件 broker 的事件記錄服務帳戶的地區設定而定。  
  
    > [!NOTE]
    >  變更記錄服務帳戶密碼時，您應該先變更中的密碼[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsAD](../../includes/btsad-md.md)]目錄服務，然後重新啟動服務後執行的每部伺服器上的記錄服務密碼變更的記錄。  
  
## <a name="see-also"></a>請參閱  
 [訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [記錄設定](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)