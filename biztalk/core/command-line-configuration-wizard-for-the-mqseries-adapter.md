---
title: "MQSeries 配接器的命令列組態精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MQSeries adapters], silent configuration
- MQSeries adapters, silent configuration
- configuring [MQSeries adapters], Command-Line Configuration Wizard
- Command-Line Configuration Wizard
- MQSeries adapters, Command-Line Configuration Wizard
ms.assetid: cab905d1-fe19-4d6a-be1b-f561e133e1d2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee73b890fca43a3651f22092486e5898862b0b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="command-line-configuration-wizard-for-the-mqseries-adapter"></a>MQSeries 配接器的命令列組態精靈
此精靈在安裝、解除安裝和記錄動作方面有四個選項。  
  
## <a name="syntax"></a>語法  
 **mqsconfigwiz [/u] [/i config.xml] [/l 記錄檔] [/？]**  
  
|選項|Description|  
|------------|-----------------|  
|**/u**|解除安裝 MQSAgent。|  
|**/i** *config.xml*|安裝 MQSAgent 使用檔案中的資訊*config.xml*。|  
|**/l** *記錄檔*|動作記錄檔案*logfile*。|  
|**/?**|顯示描述命令列選項的對話方塊|  
  
 包含組態資訊的 XML 檔案內容會依據您所使用的 Windows 版本而有所不同。 如需組態檔格式的詳細資訊，請參閱[MQSeries 配接器的 XML 組態檔](../core/xml-configuration-file-for-the-mqseries-adapter.md)。  
  
> [!IMPORTANT]
>  執行組態精靈時，配接器無法運作。  
  
> [!NOTE]
>  您無法使用命令列組態精靈來重新設定 MQSAgent。 您必須先執行精靈解除安裝代理程式 (**/u**)，然後執行它來進行設定 (**/i**)。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器的無訊息組態](../core/silent-configuration-of-the-mqseries-adapter.md)