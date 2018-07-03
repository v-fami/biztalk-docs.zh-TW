---
title: Update2XMLSchema 工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, Update2XMLSchema tool
- schemas, Update2XMLSchema tool
- Update2XMLSchema tool
- Update2XMLSchema tool, syntax
ms.assetid: fd861e2f-ebda-427f-bd52-a2f05b7e22da
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 108bc63536e84dd18cd738fbc6ec10d1e07c404b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978135"
---
# <a name="update2xmlschema-tool"></a>Update2XMLSchema 工具
Update2XMLSchema 工具可讓您修改 HL7 2.xml 結構描述來使用 BizTalk 編輯器中。 這是必要的因為某些 HL7 2.xml 結構描述無法正常運作中 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]而不需修改。 修改後的結構描述，此工具將它們放在結構描述資料夾所在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]已安裝，比方說， *\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>HL7\Templates\Schemas 的加速器。  
  
 您需要更新以手動方式從執行 Update2XMLSchema 工具所產生的結構描述中的某些欄位。 請參閱[所需的手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)如需這些結構描述的清單。  
  
## <a name="syntax"></a>語法  
 此工具位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\2XML 公用程式。 您可以執行此工具在命令提示字元中，使用下列命令：  
  
```  
Update2XMLSchema /s /v  
```  
  
 下表列出要使用此命令的參數。  
  
|參數|[屬性]|ReplTest1|  
|---------------|----------|-----------|  
|*S*|來源|原始 HL7 結構描述的完整路徑|  
|*V*|版本|2.XML 結構描述版本： 2.3.1、 2.4 或 2.5|  
  
## <a name="example"></a>範例  
  
-   如果您想要修改第 2.3.1 版 2.xml 結構描述位於 c:\231XML\v231\xsd 目錄中，您會在命令提示字元中輸入下列命令：  
  
```  
Update2XMLSchema /s c:\231XML\v231\xsd /v 2.3.1  
```  
  
## <a name="in-this-section"></a>本節內容  
  
-   [需要手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)