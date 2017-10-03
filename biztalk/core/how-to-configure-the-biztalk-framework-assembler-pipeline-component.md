---
title: "如何設定 BizTalk Framework 組合器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Assembler
- BizTalk Framework Assembler [pipeline component], configuring
ms.assetid: 2fd51047-b9dd-4b98-a968-45d69148664e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8337f5dcb2133d2a219d055751835b4ed14d379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-biztalk-framework-assembler-pipeline-component"></a>如何設定 BizTalk Framework 組合器管線元件
### <a name="to-configure-the-properties-for-the-biztalk-framework-assembler-pipeline-component"></a>設定 BizTalk Framework 組合器管線元件的屬性  
  
1.  將 BizTalk Framework 組合器管線元件拖曳到傳送管線的「組合」階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，設定下列屬性值。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**新增處理指示文字**|允許已組合的 XML 文件包含處理指示作為這個屬性的值。 也可讓文件包含應用程式的指示。 **注意：**處理指示文字應該符合 W3C XML 處理指示標準。 <br /><br /> 預設值： 附加|  
    |**新增 XML 宣告**|新增 XML 宣告到外寄訊息。 若為 true，下列 XML 宣告會新增至傳出的訊息： `<?xml version='1.0' encoding='UTF8'>`。 指定的編碼方式，取決於 BizTalk Framework 組合器，以便標示帶有編碼資訊的特定執行階段屬性所使用的編碼。<br /><br /> 預設值： **，則為 True**|  
    |**傳遞回條地址**|指定 BizTalk Framework 文件送達回條的傳送地址。 **警告：**時使用啟用通知的 BizTalk Framework 組合器，很有可能導致死結會積存認可處理。 若在個別的批次中處理單一訊息的多個確認，就會發生鎖死情況。 若要避免這個問題，您應該將輸入之送達回條地址連接埠位置的批次大小設為 1。|  
    |**送達回條地址類型**|指定 BizTalk Framework 文件送達回條的傳送地址類型。<br /><br /> 預設值： biz:**附註：** biz： 前置詞用來表示組織識別項的來源和目的端點，在 Microsoft[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]和[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]，以及與這些系統交互操作。 這是預設提供的前置詞。 例如，輸入 ="biz: OrganizationName"，(src &#124; dest) ="Party1"。|  
    |**依時間傳遞回條傳送**|指定必須收到 BizTalk Framework 文件送達回條的時間 (以分鐘為單位)。<br /><br /> 預設值： 30|  
    |**目的地位址**|指定目的地址。<br /><br /> 預設值：無|  
    |**目的地址類型**|指定目的地址類型。<br /><br /> 預設值： biz:**附註：** biz： 前置詞用來表示組織中的來源和目的地端點的識別項[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]和[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]，以及與這些系統交互操作。 這是預設提供的前置詞。 例如，輸入 ="biz: OrganizationName"，(src &#124; dest) ="Party1"。|  
    |**文件結構描述**|指示要套用到文件之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。 **注意：**如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**文件結構描述**屬性。 <br /><br /> 預設值：空集合|  
    |**文件主題**|識別 URI 參考，此參考可以唯一識別 BizTalk Framework 文件的整體目的。<br /><br /> 預設值：無|  
    |**信封結構描述**|指示要套用到信封之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。 **注意：**如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**信封結構描述**屬性。 <br /><br /> 預設值：BTF2Schemas.btf2_envelope|  
    |**產生送達回條要求**|指示是否要產生 BizTalk Framework 文件的送達回條要求。 此選項可用來確保 BizTalk Framework 傳訊功能的可靠性。<br /><br /> 預設值： **，則為 True**|  
    |**訊息的存留時間 （以分鐘為單位）**|指定訊息有效的時間量 (以分鐘為單位)。<br /><br /> 預設值： 30|  
    |**處理指示**|指定在 XML 執行個體文件中將如何處理 XML 處理指示。<br /><br /> **附加**： 的值**新增處理指示文字**應該附加到已存在訊息中的處理指示。<br /><br /> **建立新**： 的值**新增處理指示文字**輸入中的欄位應該覆寫或取代任何已存在訊息中的處理指示。<br /><br /> 如果**新建**選取時，**新增處理指示文字**必須包含有效的處理指示。<br /><br /> **忽略**： 如果存在處理指示文字訊息中，將其移除。<br /><br /> 預設值：**附加**|  
    |**來源位址**|指定來源地址。<br /><br /> 預設值：無|  
    |**來源地址類型**|指定來源地址類型。<br /><br /> 預設值： biz:**附註：** biz： 前置詞用來表示組織中的來源和目的地端點的識別項[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]和[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]，以及與這些系統交互操作。 這是預設提供的前置詞。 例如，輸入 ="biz: OrganizationName"，(src &#124; dest) ="Party1"。|  
    |**目標字元集**|指定將用來為外寄訊息編碼的目標字元集。<br /><br /> 預設值：無|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Framework 組合器管線元件](../core/biztalk-framework-assembler-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)