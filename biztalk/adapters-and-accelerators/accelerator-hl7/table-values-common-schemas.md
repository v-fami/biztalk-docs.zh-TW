---
title: "資料表值的通用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, common schemas
- 2.X schemas, table values
- common schemas
ms.assetid: 2421e150-1bae-43bd-aba3-6322c679b22b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b93434c57988b8ef0cdb068ffb960e6fb342edc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="table-values-common-schemas"></a>資料表值的通用結構描述
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會產生 **tablevalues_*\<版本 >*.xsd * * 如需每個 HL7 版本中，檔案中，並找出 HL7 根目錄的檔案特定版本的資料夾。 資料類型通用的結構描述檔案參考的資料表值 common 結構描述檔案。  
  
 這些資料表中的值是列舉型別的格式。 每個列舉會定義可接受之訊息結構描述的一或多個欄位內的值。 您可以查看哪一個資料表套用到訊息結構描述的節點，BizTalk 編輯器中開啟結構描述中，按一下節點，並查看**基底資料型別**屬性 窗格中的屬性。  
  
 您無法檢視此節點可接受的值為何，不過，藉由檢視訊息結構描述節點屬性 窗格中的列舉型別。 這是因為資料表值 common 結構描述檔案會定義列舉型別。 若要檢視的列舉型別，請按一下 **tablevalues_*\<版本 >*.xsd * * 在結構描述樹狀結構中 [BizTalk 編輯器] 中，，，然後按一下省略符號 (**...**) 列舉中的資料列 [屬性] 窗格上的按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 2.X 通用結構描述檔案](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [資料類型的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md)   
 [區段的一般結構描述](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)