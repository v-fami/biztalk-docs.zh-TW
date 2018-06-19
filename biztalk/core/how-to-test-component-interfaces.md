---
title: 如何測試元件介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing component interfaces
- component interfaces, testing
ms.assetid: d637f76d-170d-4543-a2b2-a4ac4001386b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be50521e5c4421d8ac8902bcf7a414d734c3b9f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256566"
---
# <a name="how-to-test-component-interfaces"></a>如何測試元件介面
Microsoft BizTalk Adapter for PeopleSoft Enterprise 使用 PeopleSoft 中繼資料和元件介面；因此，它可以處理新的或已修改的元件介面。 配接器對元件介面不做任何限制性規定，但是除了元件介面必須符合邏輯且有效。 因此，每個元件介面做為配接器的來源之前，都必須先進行測試。  
  
 如果因使用者或 PeopleSoft 升級而使得基礎應用程式發生變更，同時這些變更造成元件介面失效，這時使用者必須修復無效的元件介面，才能提供配接器使用。  
  
### <a name="to-test-a-component-interface"></a>若要測試元件介面  
  
1.  在 應用程式設計工具上**工具**功能表上，按一下  **Test Component Interface**。  
  
     ![](../core/media/psadapter-54-ps-testcompinterface1.gif "PSAdapter_54_PS_TestCompInterface1")  
  
2.  在**Component Interface Tester**對話方塊方塊中，使用下列方法測試元件介面。 完成變更之後，以滑鼠右鍵按一下窗格中最上方的項目。  
  
    > [!NOTE]
    >  若有必要，請按一下該對話方塊使其顯示於前景。  
  
    -   若要測試元件介面使用 Find 方法，請按一下**尋找**。  
  
         **Component Interface Tester-尋找結果** 對話方塊隨即開啟，顯示基礎元件的所有可能的項目。 如果有超過 300 個項目，則會顯示訊息。  
  
         a. 在左窗格中**尋找結果**對話方塊中，選取一個欄位。  
  
         b. 若要顯示該特定欄位的相關資料，請按一下**Get Selected**。  
  
         下列畫面隨即出現。  
  
         ![](../core/media/psadapter-55-ps-testcompinterface2.gif "PSAdapter_55_PS_TestCompInterface2")  
  
         如果安全性設定允許的話，您可以變更個別欄位中的值。  
  
         下列對話方塊隨即開啟。  
  
         ![](../core/media/psadapter-56-ps-testcompinterface3.gif "PSAdapter_56_PS_TestCompInterface3")  
  
    -   若要使用 `Get` 方法測試元件介面：  
  
         a. 輸入現有金鑰。  
  
         b. 按一下**取得現有**。  
  
         這會傳回所輸入金鑰的已公開屬性。  
  
         您可以變更值，如果**更新存取**指定。  
  
         或者，您可以使用 `Create` 方法進行測試。  
  
         ![](../core/media/psadapter-57-ps-testcompinterface4.gif "PSAdapter_57_PS_TestCompInterface4")  
  
    -   若要使用 `Create` 方法測試元件介面：  
  
         a. 輸入所有必要的金鑰值。  
  
         b. 按一下**建立新**。  
  
         當您輸入有效的值**建立金鑰**，顯示 JOBCODE 資料 窗格會開啟預設的資料，就地展開資料表名稱之後。  
  
         現在您可以變更欄位。  
  
         ![](../core/media/psadapter-58-ps-testcompinterface5.gif "PSAdapter_58_PS_TestCompInterface5")  
  
         此作業會針對元件的基礎商務邏輯來驗證變更。  
  
3.  若要儲存您的變更，請按一下**儲存**圖示。  
  
     用來建立記錄的金鑰可以與 Get 方法搭配使用，以檢視資料。 所加入的資料可從 PeopleSoft 元件進行檢視，如下列範例所示。  
  
     ![](../core/media/psadapter-59-ps-testcompinterface6.gif "PSAdapter_59_PS_TestCompInterface6")  
  
     **生效日期**是其中一個預設值。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)   
 [附錄 c： 使用元件介面](../core/appendix-c-using-component-interfaces.md)