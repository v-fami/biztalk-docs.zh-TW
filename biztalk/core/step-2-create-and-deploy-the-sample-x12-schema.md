---
title: 步驟 2： 建立和部署範例 X12 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5862168-6621-40ab-8c97-3f317530d34e
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57c95ac64637027b5d39699a42e8fac93c003697
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974468"
---
# <a name="step-2-create-and-deploy-the-sample-x12-schema"></a>步驟 2： 建立和部署範例 X12 結構描述
![步驟 2 的 11](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")  
  
 在此步驟中，您將建置和部署可提供範例 EDI X12 結構描述的專案，該結構描述是處理透過 AS2 傳輸之內送 EDI X12 交換的必要項目。 在本教學課程中，該結構描述為 X12_00401_864.xsd。 您不必變更 AS2 教學課程隨附的專案，只要直接建置即可。  
  
> [!NOTE]
>  本教學課程使用的結構描述檔 X12_00401_864.xsd 是儲存在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas 資料夾中。 它已經加入到您將在此步驟中建置和部署的 Schemas 專案內。 此結構描述不同於執行 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾中的 MicrosoftEdiXsdTemplates	.exe 時下載到電腦上的 X12_00401_864.xsd 檔案。 您必須使用已加入到 Schemas.btproj 中的 X12_00401_864.xsd 檔案，才可以執行本教學課程。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-create-and-deploy-the-sample-x12-schema"></a>若要建立和部署範例 X12 結構描述  
  
1.  啟動**Microsoft Visual Studio**身為系統管理員。  
  
2.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟解決方案 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
3.  結構描述專案中，按一下滑鼠右鍵，然後按一下**屬性**。 按一下**簽署**專案設計工具中的索引標籤。 請檢查**簽署組件**核取方塊，如**選擇強式金鑰名稱檔**，選取**\<新增...\>** 輸入`Schemas.snk`。 清除**保護我的密碼金鑰檔**，然後按一下 **確定**。 關閉專案屬性對話方塊並儲存所做的變更。  
  
4.  建置並部署 Schemas.btproj。  
  
## <a name="next-steps"></a>後續步驟  
 中所述，為您的組織 (Contoso)，設定合作對象與商務設定檔[步驟 3： 設定適用於您組織的合作對象與商務設定檔](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md)。  
  
## <a name="see-also"></a>請參閱  
 [EDI 文件結構描述](../core/edi-document-schemas.md)