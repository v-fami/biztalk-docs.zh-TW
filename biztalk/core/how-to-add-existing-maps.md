---
title: 如何新增現有的對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbeaea05-016e-488c-90f3-af8c6b9a3d84
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a61fb0faf5f4eed614257361b00cea781db2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247454"
---
# <a name="how-to-add-existing-maps"></a>如何新增現有的對應
您可能時常要新增現有的對應到 BizTalk 專案。 在進行之前，您必須確定對應的來源與目的結構描述都包含在您要新增對應的 BizTalk 專案中；或者，由對應的 .NET 組件所參考。  
  
### <a name="to-add-an-existing-map-to-a-biztalk-project"></a>新增現有的對應到 BizTalk 專案  
  
1.  以滑鼠右鍵按一下方案總管] 中的 BizTalk 專案，指向**新增**，然後按一下 [**現有項目**。  
  
2.  在**加入現有項目**對話方塊中，瀏覽至包含以加入、 選取它，然後按一下對應的資料夾**新增**。  
  
     對應就會在 BizTalk 對應工具中開啟。 新增的對應也會顯示為 [方案總管] 中目前 BizTalk 專案的子項目。  
  
    > [!NOTE]
    >  若您瀏覽至 BizTalk 專案資料夾以外的資料夾，則會在專案資料夾中建立您所新增對應的複本，而加入專案中的對應就是此複本。 後續的對應變更會在此複本進行，而不是其他資料夾中的原始對應。  
  
    > [!IMPORTANT]
    >  BizTalk 對應只能開啟 BizTalk 對應工具，裝載於 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]殼層。 若按兩下 Windows 檔案總管中的對應，將會開啟新的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 執行個體，只要相對應的結構描述正確載入，[BizTalk 對應工具] 就會開啟對應。  
  
    > [!NOTE]
    >  如果現有的對應包含自訂運算質，則相對應的 DLL 必須複製到資料夾 “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”。 否則，非但不會載入對應，還會擲回錯誤，因為無法載入自訂運算質。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的對應](../core/managing-maps-within-projects.md)   
 [開發自訂運算質](../core/developing-custom-functoids.md)