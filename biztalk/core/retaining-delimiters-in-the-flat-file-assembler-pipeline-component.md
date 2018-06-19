---
title: 保留一般檔案組合器管線元件中的分隔符號 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adc27561-9996-49a9-b715-e313b9148506
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9d10879adfbe0ca0c68376faa48d9976fc19599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268782"
---
# <a name="retaining-delimiters-in-the-flat-file-assembler-pipeline-component"></a>在一般檔案組合器管線元件中保留分隔符號
如果在通過使用一般檔案組合器之自訂管線的訊息中有遺失的記錄，則一般檔案輸出中不一定會出現這些記錄的分隔符號，這要取決於這些記錄在輸入檔案中的遺失位置而定。  
  
 為了確保一般檔案會保留某些分隔符號，您可以使用對應和自訂指令碼，以確定當訊息中沒有特定的輸入記錄存在時，會建立「空的」記錄。 為了要讓這樣的處理方式可行，您必須確保一般檔案組合器之文件結構描述中可能是空的節點有設定下列屬性：  
  
|屬性|設定|  
|--------------|-------------|  
|保留空白資料的分隔符號|是|  
|隱藏尾端分隔符號|否|  
|產生空節點 (在根節點上設定)|True|  
  
### <a name="to-create-a-map-that-creates-an-empty-record"></a>若要建立會建立空記錄的對應  
  
1.  將新的對應加入到 BizTalk 專案。  
  
2.  將一般檔案組合器使用的文件結構描述指定為對應來源和對應目的結構描述。  
  
3.  將不是空的來源欄位對應到相對應的目的欄位。  
  
4.  如果是那些可能是空的欄位，請使用自訂指令碼來檢查來源欄位是不是空的，然後傳回空字串 (而不是 Nil)。 請使用類似以下的指令碼：  
  
    ```  
    public string ValOrEmpty(string val)  
    {  
         return (val.Length > 0) ? val : "";  
    }  
    ```  
  
    > [!NOTE]
    >  您必須針對每一個可能是空的對應欄位建立具有唯一函式名稱的指令碼。 例如，如果有三個欄位可能是空的，您可能會有名為 `ValOrEmpty1`、`ValOrEmpty2`、`ValOrEmpty3` 的函式。  
  
5.  使用 BizTalk Server 管理主控台來設定具有自訂管線的傳送埠以及一般檔案組合器元件，將此對應當做輸出對應來使用。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定傳送埠的輸出對應](../core/how-to-configure-outbound-maps-for-a-send-port.md)   
 [一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md)