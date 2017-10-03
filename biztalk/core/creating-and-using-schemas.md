---
title: "建立和使用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas
- creating schemas
- schemas, generating
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f10275c5ed0b887907c7b26b7d1ce8ad5003b099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-using-schemas"></a>建立和使用結構描述
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 會使用您利用 XML 編輯器或 Visual Studio 的 BizTalk Server 編輯器 (僅限當您在協調流程中使用配接器時) 建立的結構描述。 結構描述說明您預期的資訊類型。 本主題包含傳送與接收處理常式的資訊。  
  
 您建立來與 BizTalk Adapter for TIBCO Enterprise Message Service 搭配使用的結構描述必須有目標命名空間。 BizTalk Server 需要目標命名空間，因為那是讓指定的訊息執行個體與指定的協調流程產生關聯的索引鍵。 換句話說，協調流程會訂閱擁有特定目標命名空間的任何訊息，而含有該目標命名空間的內送 XML 訊息會提供給訂閱該訊息的每個協調流程。 如果 XML 文件結構描述沒有目標命名空間，BizTalk Server 會使用根項目的名稱做為索引鍵。  
  
## <a name="generating-a-schema"></a>產生結構描述  
 下列程序說明如何產生結構描述，以及如何設定目標命名空間。  
  
#### <a name="to-generate-a-schema-using-biztalk-editor"></a>使用 BizTalk 編輯器產生結構描述  
  
1.  在 [BizTalk 編輯器] 中開啟專案。  
  
2.  在 [方案總管] 右上方中，選取**新增**，然後選取**新增產生的項目**。  
  
3.  在**範本**窗格中，選取**產生結構描述**，然後按一下 **新增**。  
  
4.  在**產生結構描述**對話方塊中，於**文件類型**清單中，選取**格式正確的 XML**。  
  
5.  按一下**瀏覽**找出您要產生結構描述，然後輸入的檔案**確定**。  
  
     接下來，您必須設定目標命名空間。  
  
#### <a name="to-set-the-target-namespace"></a>設定目標命名空間  
  
1.  在 [BizTalk 編輯器] 中，開啟結構描述檔案，以滑鼠右鍵按一下**\<結構描述 >**，然後選取**屬性**。  
  
2.  在**屬性** 窗格中，找出**命名空間**欄位並輸入名稱，例如`testNameSpace`。  
  
 您之後可以使用訊息繼續您的協調流程。 在挑選訊息後，BizTalk Server 會尋找使用的結構描述具有所設定目標命名空間的協調流程，接著進行協調流程程序。  
  
## <a name="see-also"></a>另請參閱  
 [開發應用程式](../core/developing-applications5.md)