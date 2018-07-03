---
title: 驗證結構描述 (EDI) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6175460-2dcf-4fef-b770-02f0a058bf93
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12f54b77420a9e03e701c5e154bba681b46c166c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997511"
---
# <a name="validating-a-schema-edi"></a>驗證結構描述 (EDI)
您可以在設計階段驗證 EDI 結構描述。 若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。 驗證結構描述作業會根據 EDI 規則來驗證結構描述。 因此，您不必指定輸入訊息執行個體來驗證結構描述。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-validate-a-schema"></a>若要驗證結構描述  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。 在 [方案總管] 中，將您要驗證的訊息結構描述加入至該專案中。  
  
   > [!NOTE]
   >  訊息結構描述位於底下的適當子資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾。 如需安裝的結構描述檔案的詳細資訊，請參閱[如何安裝 EDI 結構描述檔案](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550)。  
   > 
   > [!NOTE]
   >  您不必建置專案來驗證結構描述。  
  
2. 以滑鼠右鍵按一下方案總管 中的結構描述，然後按一下**驗證結構描述**。  
  
3. 確認 [輸出] 視窗中有指出作業成功的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)