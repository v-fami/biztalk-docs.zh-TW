---
title: "建立和部署原則的新訊息類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43343238-ec45-44ed-a230-9e234bd22d05
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b89972b2b84927fc16b14184338ca4920e984656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-deploying-policies-for-new-message-types"></a>建立和部署原則的新訊息類型
若要建立並部署新的訊息類型的原則：  
  
1.  建立 MX 訊息資料夾內的訊息類型名稱的資料夾。 例如，在此情況下名稱會是資料夾的 setr.004.001.02。  
  
    ```csharp  
    (<xs:complexType name="Document">  
        <xs:sequence>  
            <xs:element name="setr.004.001.02" type="setr.004.001.02"/>  
        </xs:sequence>  
    </xs:complexType>)  
    ```  
  
2.  將結構描述檔案 (*.xsd)，以及產生的主要 / 驗證原則檔，以取得此訊息類型，此資料夾中。  
  
3.  更新關鍵字名稱 MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools)。 此名稱必須是訊息的資料夾名稱的前四個字母。 例如，  
  
    ```csharp  
    (<Keyword name ="setr" />)  
    ```  
  
4.  若要建立特定的主要 / 驗證原則，製作的主要複本] / [現有的驗證原則檔訊息，並將它放在新的郵件資料夾。  
  
5.  在 master 中的訊息類型參考的所有變更 / 驗證原則，以反映新的訊息類型。  
  
## <a name="message-naming-conventions"></a>訊息的命名慣例  
 請依照下列訊息名稱的這些的慣例：  
  
-   **將訊息名稱取代**： 如果新的訊息名稱是 swift.if.ia.setr.004.001.02，舊的原則檔都已使用的訊息是 pacs.002.001.02 然後取代所有與 pacs.002.001.02 的項目swift.if.ia.setr.004.001.02 原則檔案中。  
  
    > [!NOTE]
    >  訊息名稱是已下載的結構描述檔案的名稱，而且訊息類型的訊息中的文件類型名稱。  
  
-   保留原則檔案的名稱與相同的訊息結構描述本身。 例如，swift.if.ia.setr.004.001.02.xsd 會有下列原則 swift.if.ia.setr.004.001.02 _Master_Policy.xml 和 swift.if.ia.setr.004.001.02 _Validation_Policy.xml。  
  
-   **特殊字元**： 如果訊息名稱中，有任何特殊字元，則建立的原則檔，需要稍微不同的慣例。 如果訊息名稱，比方說，swift.if.ia$setr.004.001.02，則您必須以訊息名稱變更原則檔案的名稱，含有要取代特殊字元"。" 例如，如果 swift.if.ia$setr.004.001.02.xsd 訊息結構描述檔案的名稱，則產生的主要原則是 swift.if.ia.setr.004.001.02_Master_Policy.xml。  
  
     主要的原則檔也需要變更以反映新的名稱，在下列標記：  
  
    -   \<ruleset name="swift.if.ia.setr.004.001.02_Master_Policy">  
  
    -   < 規則 name="swift.if.ia.setr.004.001.02_Policy_List"