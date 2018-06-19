---
title: Update2XMLSchema 工具 |Microsoft 文件
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
ms.openlocfilehash: e0f5a33b8951d1f02cf0504ba833b35adf275834
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961108"
---
# <a name="update2xmlschema-tool"></a>Update2XMLSchema 工具
Update2XMLSchema 工具可讓您修改 HL7 2.XML 結構描述，才能使用 「 BizTalk 編輯器。 這是必要的因為某些 HL7 2.XML 結構描述無法正確內運作[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]而不需修改。 在修改後結構描述，此工具放入結構描述資料夾其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝時，比方說， *\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\Templates\Schemas。  
  
 您需要更新以手動方式從執行 Update2XMLSchema 工具產生的結構描述中的某些欄位。 請參閱[所需的手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)如需這些結構描述的清單。  
  
## <a name="syntax"></a>語法  
 此工具位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\2XML 公用程式。 您可以執行此工具在命令提示字元使用下列命令：  
  
```  
Update2XMLSchema /s /v  
```  
  
 下表列出使用此命令的參數。  
  
|參數|名稱|值|  
|---------------|----------|-----------|  
|*S*|Source|原始 HL7 結構描述的完整路徑|  
|*V*|Version|2.XML 結構描述的版本： 2.3.1、 2.4 或 2.5|  
  
## <a name="example"></a>範例  
  
-   如果您想要修改版本 2.3.1 2.XML 結構描述位於 c:\231XML\v231\xsd 目錄中，您會在命令提示字元輸入下列命令：  
  
```  
Update2XMLSchema /s c:\231XML\v231\xsd /v 2.3.1  
```  
  
## <a name="in-this-section"></a>本節內容  
  
-   [需要手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)