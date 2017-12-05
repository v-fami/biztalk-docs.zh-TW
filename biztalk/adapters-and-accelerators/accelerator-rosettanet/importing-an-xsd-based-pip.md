---
title: "匯入以 XSD 為基礎的 PIP |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, importing
- XSD-based PIPs
- PIPs, XSD-based PIPs
ms.assetid: d12441d4-79bf-4c24-9360-4b78c1da0d34
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d8865d7a75bdb06895b963b8269ed457cd5804f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="importing-an-xsd-based-pip"></a>匯入以 XSD 為基礎的 PIP
雖然由 RosettaNet.org 提供的 PIP 大部分是以 DTD 為基礎，但較新的 PIP 則是以 XSD 為基礎。 下列程序說明如何匯入以 XSD 為基礎的 PIP。  
  
### <a name="to-import-an-xsd-based-pip"></a>匯入以 XSD 為基礎的 PIP  
  
1.  從 RosettaNet.org 在下載以 XSD 為基礎的 PIP.zip 檔案[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859)或從 CIDX.org 在[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361)。 從 .zip 檔解壓縮這些檔案。 您需要的檔案是放在 [XML] 資料夾的子資料夾中。  
  
2.  開啟 Visual Studio。 建立新的 BizTalk 專案。  
  
3.  開啟 [Windows 檔案總管]，移至在步驟 1 所解壓縮的 XML 資料夾。 選取 XML 資料夾下的第一個資料夾，將它拖曳到 Visual Studio 的 [方案總管] 中，並且放置在您的專案中。 對 [XML] 資料夾中的每一個子資料夾重複上述動作，在您的專案中建立相同的資料夾結構。  
  
    > [!NOTE]
    >  對於 PIP7c7 PIP，這些資料夾會包括 [Domain]、[Interchange]、[System] 和 [Universal] 資料夾。 對於這個 PIP，您的專案應該包含 [Domain]、[Interchange]、[System] 和 [Universal] 資料夾及其內容。  
  
4.  如果在 [System] 資料夾中有 .xsd 檔案，請在 [方案總管] 中選取它，並且變更屬性頁面中所列的命名空間，使它不包含字串 ".System"。 例如，對於 PIP7c7 PIP，您可以將命名空間變更為 "PIP7c7._System"。 對 [System] 資料夾中的每一個 .xsd 檔案重複上述動作。 如果您不變更命名空間，您將會看到類似下列的錯誤訊息：  
  
    ```  
    The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'PIP7C7.System'.  
    ```  
  
5.  檢閱所有.xsd 檔案，請確認\<結構描述\>TypeName 和根節點 TypeName 不相同。 例如，對於 PIP7C7 PIP PartnerIdentification.xsd Universal 資料夾中的有 'PartnerIdentification' 的 TypeName 兩個\<結構描述\>（當在方案總管 中選取 PartnerIdentification.xsd） 以及PartnerIdentification 根節點。 若要更正這種情況，請在 [方案總管] 中選取 PartnerIdentification.xsd，然後變更屬性頁面中的 TypeName 屬性，使它不會包含與 PartnerIdentification 根節點相同的 TypeName。 例如，將 TypeName 變更為 "_PartnerIdentification"。 如果不執行這個步驟，當您嘗試建置專案時便會看到下列錯誤訊息：  
  
    ```  
    Node "<Schema>" - This schema file has a TypeName that collides with the RootNode TypeName of one of its root Nodes. Make sure that they are different.  
    ```  
  
    > [!NOTE]
    >  錯誤清單中的 [檔案] 欄位將會顯示哪些檔案發生這個問題。  
  
6.  建置然後再部署專案。