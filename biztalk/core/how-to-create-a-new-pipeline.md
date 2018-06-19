---
title: 如何建立新管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, warnings
- Pipeline Designer, warnings
- pipelines, creating
ms.assetid: bd95325e-1a72-4705-80f6-37ac092d11a3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83c1df14c0015ac26b99ad8f0760fe18438e8024
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248758"
---
# <a name="how-to-create-a-new-pipeline"></a>如何建立新的管線
您可以新增管線範本到您的專案，以建立新管線。  
  
> [!WARNING]
>  您不應該新增包含的實作包含使用該管線元件專案的方案到自訂管線元件的專案。 如果您這樣做，下次重新建置方案時，就會收到錯誤訊息，指出輸出 dll 已被其他程序使用。  
  
### <a name="to-create-a-new-pipeline"></a>建立新管線  
  
1.  在 [方案總管] 中選取您想在其中建立管線的專案。  
  
2.  在 [專案] 功能表上，按一下 [加入新項目]。  
  
3.  在**加入新項目**對話方塊中，選取**接收管線**或**傳送管線**範本即可一次。  
  
    > [!NOTE]
    >  如果您按兩下範本，將會自動使用預設的名稱會出現在建立管線**名稱**欄位。  
  
4.  在**名稱**欄位中，輸入管線的名稱。  
  
5.  按一下 **[開啟]**。  
  
     新管線隨即出現在 [方案總管] 中。 設計介面會顯示管線階段和預設元件組。  
  
 新增管線元件至管線的相關資訊，請參閱[如何新增元件至管線](../core/how-to-add-a-component-to-a-pipeline.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何開啟管線](../core/how-to-open-a-pipeline.md)   
 [如何儲存管線](../core/how-to-save-a-pipeline.md)   
 [如何使用 [工具箱]](../core/how-to-use-the-toolbox.md)   
 [如何使用鍵盤巡覽](../core/how-to-navigate-with-the-keyboard.md)   
 [使用管線設計師建立管線](../core/creating-pipelines-with-pipeline-designer.md)