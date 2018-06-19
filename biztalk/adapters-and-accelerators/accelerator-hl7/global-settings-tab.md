---
title: 全域設定 索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.globalsettings
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- Global Settings tab [Configuration Explorer]
- auditing, configuring
ms.assetid: 057189f7-9072-4841-950f-371ba1f73a15
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 022ad14cc93b55c7ad928c06358f2714531b40b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204894"
---
# <a name="global-settings-tab"></a>全域設定 索引標籤
您使用**通用設定**索引標籤以設定所使用的記錄存放區[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]。  
  
 在**BTAHL7 Configuration 總管**對話方塊**通用設定**索引標籤上，執行下列動作：  
  
|使用|動作|  
|--------------|----------------|  
|**WMI**|選取此選項，如果您想要產生[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]BTAHL7 的 Management Instrumentation (WMI) 通知。|  
|**SQL**|選取此選項，如果您想要使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]為 BTAHL7 您記錄存放區。 **注意：** BTAHL7 會自動建立所需的記錄，如果它們尚不存在的資料表。|  
|**[SQL Server]**|型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]名稱。 這是必要的當您選取**SQL**選項。 允許的長度上限為 64 個字元。<br /><br /> 預設的伺服器和資料庫名稱是已設定的 BTAHL7 資料庫。|  
|**資料庫名稱**|型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫名稱。 這是必要的當您選取**SQL**選項。 最大允許的長度為 128 個字元。|  
|**事件記錄檔**|選取此選項，如果您想要使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]BTAHL7 的記錄存放區為事件記錄檔。 您使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器來檢視事件訊息。|