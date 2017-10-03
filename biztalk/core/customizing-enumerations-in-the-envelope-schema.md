---
title: "自訂列舉信封結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b053d82-753f-4a05-9922-fa5dbd073ba9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b33458d3a7fbc71ea5e2df7603390f10b928113
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-enumerations-in-the-envelope-schema"></a>在信封結構描述中自訂列舉
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您自訂識別碼欄位列舉服務 （信封） 結構描述中。 如此可讓您接收或傳送信封的寄件者或接收者識別碼欄位中擁有非標準值 (在 X12 標準組織所定義的值集合以外) 的交換。 它也可讓您變更協議屬性定義中的標頭值的下拉式清單中可用的限定詞。  
  
> [!IMPORTANT]
>  當您修改結構描述時，該修改會套用至實際標準的所有交易。 您無法在單一合作對象的信封結構描述進行修改。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會從靜態服務結構描述的允許值的清單提取與產品隨附的 Microsoft.BizTalk.Edi.BaseArtifacts.dll 中。 若要擴充基本的值集合，您需要開發和部署服務結構描述延伸模組。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供服務 （信封） 結構描述範本，可用來修改在列舉型別。 這些服務結構描述是 X12_ServiceSchemaExtension.xsd 和 EDIFACT_ServiceSchemaExtension.xsd。 根據標準而定，每個自訂結構描述都會有下列其中一個命名空間。 這個命名空間無法變更。  
  
|Standard|命名空間|  
|--------------|---------------|  
|X12 和 HIPAA|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006`|  
|EDIFACT|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`|  
  
 您對結構描述在 BizTalk 編輯器中變更[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]（請參閱下列程序）。 完成需要的變更之後，必須部署結構描述。  
  
 在接收和傳送端上時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]驗證信封區段 （ISA 和 GS X12，或 UNB 和 UNG edifact），它會檢查它的命名空間為基礎的自訂服務結構描述是否存在。 如果部署自訂結構描述，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將合併該結構描述與一般服務結構描述，且將會使用自訂和標準列舉所指定的值。 您可以自訂結構描述以擴充列舉清單，但是無法移除清單中的值。 如果未部署自訂結構描述，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將使用標準服務結構描述。  
  
 當您部署自訂結構描述之後,[!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)]中的使用者介面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台會使用自訂列舉中的值來填入適當的下拉式清單中[!INCLUDE[TPM_abbrev](../includes/tpm-abbrev-md.md)]屬性頁。 如果您尚未部署自訂結構描述，[!INCLUDE[TPM_abbrev](../includes/tpm-abbrev-md.md)]會使用標準服務結構描述中列舉的值。 此外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段會使用自訂列舉驗證訊息。  
  
 如果您使用提供的 XML 工具[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]驗證與執行個體及其信封，而且您已自訂服務結構描述中，您還必須將自訂服務結構描述在 BizTalk 專案中，除了文件 （交易集）結構描述，如有必要，批次結構描述。 如果您要驗證沒有信封的交易集執行個體，則不需要這樣做。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
##  <a name="BKMK_Env_Can"></a>您可以修改的信封欄位  
 只有下列信封欄位才能修改。 延伸模組結構描述中只包含這些欄位。 在服務延伸模組結購描述中加入其他欄位，對於處理程序不會有任何影響。  
  
|Standard|欄位|  
|--------------|-----------|  
|X12 和 HIPAA|ISA01 – 授權辨識符號<br /><br /> ISA03 – 安全性辨識符號<br /><br /> ISA05 – 傳送者識別碼辨識符號<br /><br /> ISA07 - 接收者識別碼辨識符號<br /><br /> GS01 - 功能代碼<br /><br /> GS07 - 負責單位|  
|EDIFACT|UNB2.2 - 傳送者代碼辨識符號<br /><br /> UNB3.2 - 接收者代碼辨識符號|  
  
## <a name="envelope-fields-that-should-not-be-modified"></a>不應該修改的信封欄位  
 信封中的某些欄位會驅動引擎的行為。 因此，您不應該新增值至這些欄位的現有列舉清單。 這些欄位包括：  
  
|Standard|欄位|  
|--------------|-----------|  
|X12 和 HIPAA|ISA11 – 交換控制標準識別項<br /><br /> ISA12 – 交換控制版本號碼<br /><br /> ISA14 – 要求認可|  
|EDIFACT|UNB1.1 – 語法識別項<br /><br /> UNB1.2 – 語法版本號碼<br /><br /> UNB9 – 通知要求|  
  
### <a name="to-customize-an-enumeration-in-the-envelope-schema"></a>在信封結構描述中自訂列舉  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立新的專案。  
  
2.  在 [BizTalk 編輯器] 中，將 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 中的 X12_ServiceSchemaExtension.xsd 結構描述 (若要修改 X12 或 HIPAA 列舉) 或 EDIFACT_ServiceSchemaExtension.xsd 結構描述新增至 BizTalk 專案。 開啟結構描述。  
  
3.  若要變更列舉中的值，選取 [在列舉**屬性**] 窗格中，然後按一下省略符號以開啟**列舉型別編輯器**。 視需要加入至值的清單，確認都有一個值中的每一行**值**窗格。 按一下 **[確定]**。  
  
    > [!IMPORTANT]
    >  您無法變更服務結構描述的命名空間。 結構描述的命名空間和根節點名稱，應該與隨產品安裝的原始延伸模組結購描述相同。  
  
    > [!NOTE]
    >  如果您原本是要將新欄位加入至結構描述中，則可能會忽略該欄位。 中列出的欄位[信封欄位，才能修改](../core/customizing-enumerations-in-the-envelope-schema.md#BKMK_Env_Can)可以變更上述一節。  
  
4.  儲存結構描述。  
  
5.  以滑鼠右鍵按一下結構描述，然後按一下**部署**。  
  
    > [!NOTE]
    >  結構描述必須部署至目前的 BizTalk 群組中。  
  
## <a name="see-also"></a>另請參閱  
 [開發 EDI 結構描述](../core/developing-edi-schemas.md)   
 [修改 EDI 結構描述](../core/modifying-edi-schemas.md)