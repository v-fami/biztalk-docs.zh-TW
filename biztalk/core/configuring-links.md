---
title: 設定連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10050c28-0944-4073-afd2-54cd6c8d79a2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9926a7bdd890f75935014a79ff3994230c2378c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015695"
---
# <a name="configuring-links"></a>設定連結

## <a name="overview"></a>概觀
在顯示的格線頁中選取連結時，連結的屬性會顯示在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗中。 如需與連結相關聯之屬性的參考資訊，請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 

## <a name="source-target-and-label"></a>來源、 目標和標籤  
 下列屬性會設定對應中的連結：  
  
- **來源連結**。 您使用**來源連結**屬性可設定從輸入執行個體訊息將會用來建構輸出執行個體訊息資料的本質。 依照預設且最常用的選擇為使用輸入執行個體訊息的項目或屬性值。 也有其他選擇，包括使用輸入執行個體訊息的項目名稱或屬性。 如需有關這個屬性，及其可用選項的詳細資訊，請參閱 <<c0>  **連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
- **目標連結**。 您使用**目標連結**設定 BizTalk 對應工具如何比對節點階層層級的屬性。 依照預設，當輸出執行個體訊息建立時，會簡維來源結構描述階層。 您也可以選擇保留階層，由上往下或由下往上比對連結。 如需有關這個屬性，及其可用選項的詳細資訊，請參閱 <<c0>  **連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
- **標籤**。 您使用**標籤**屬性，以建立連結預設會使用 XPath 值更容易閱讀的名稱。 當連結用以作為表格驅動迴圈的輸入時，設定此屬性特別有用。 如需有關這個屬性，其可用的選項，以及表格驅動迴圈的詳細資訊，請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 另請參閱[表格迴圈和表格擷取程式運算質](../core/table-looping-and-table-extractor-functoids.md)分別。  
  
## <a name="see-also"></a>另請參閱  
  [如何編輯連結屬性](../core/how-to-edit-link-properties.md)