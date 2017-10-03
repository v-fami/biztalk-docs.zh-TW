---
title: "使用內嵌 XSLT 與 XSLT 呼叫範本指令碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3168417-3653-4c9e-a09c-184ffdc0ccb2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7c4c1d8eff582d15f9ce022053b80f2dea2f856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-inline-xslt-and-xslt-call-templates"></a>使用內嵌 XSLT 與 XSLT 呼叫範本的指令碼處理
您可以直接編寫用於可延伸樣式表語言轉換 (XSLT) 樣式表**指令碼處理**運算質。 如此可讓您執行轉換，而連結與內建的運算質可能不會顯示。 XSLT 指令碼分為兩種：內嵌 XSLT 與 XSLT 呼叫範本。 選取任一種**選取指令碼類型**下拉式清單中的**設定指令碼處理運算質**對話方塊中，範例程式碼會顯示您可以使用。  
  
 內嵌 XSLT 指令碼與 XSLT 呼叫範本可能呼叫外部組件中的函式。 進行這種呼叫需要設定**自訂延伸模組 XML**方格的屬性。 如需詳細資訊，請參閱**自訂延伸模組 XML （格線屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="inline-xslt"></a>內嵌 XSLT  
 內嵌 XSLT 指令碼可能只產生輸出。 **指令碼處理**運算質可能沒有任何輸入的連結。 運算質還必須直接連結到目的結構描述中的記錄或欄位。  
  
 此外，指令碼還負責建立目標節點及其之下的任何結構。  
  
 下列輸入執行個體訊息包含代表連絡資訊的兩個項目。  
  
```  
<ns0:SourceInstance xmlns:ns0="http://SourceInstanceNamespace">  
    <Address>  
        <Contact>Karin Zimprich</Contact>  
        <ContactType>Referral</ContactType>  
    </Address>  
</ns0:SourceInstance>  
```  
  
 下列內嵌 XSLT 指令碼，在指令碼緩衝區中，輸入將轉換**連絡人**和**ContactType**屬性的欄位。  
  
```  
<ContactInfo xmlns:p="http://SourceInstanceNamespace">  
     <xsl:variable name="var:var1" select="/p:SourceInstance/Address/ContactType" />  
     <xsl:attribute name="ContactType">  
          <xsl:value-of select="$var:var1" />  
     </xsl:attribute>  
     <xsl:variable name="var:var2" select="/p:SourceInstance/Address/Contact" />  
     <xsl:attribute name="Contact">  
          <xsl:value-of select="$var:var2" />  
     </xsl:attribute>  
</ContactInfo>  
```  
  
 在針對先前的輸入執行個體訊息執行時，此指令碼產生下列輸出 (假設為適當的輸出結構描述)。  
  
```  
<ns0:OutInstance xmlns:ns0="http://More_XSLT.Out">  
    <ContactInfo ContactType="Referral" Contact="Karin Zimprich" xmlns:p="http://SourceInstanceNamespace">  
    </ContactInfo>  
</ns0:OutInstance>  
```  
  
 請注意，缺少連結**指令碼處理**運算質不會防止 XSLT 指令碼從輸入執行個體訊息中取得資料。 此指令碼指定輸入執行個體值的路徑。  
  
 如需內嵌 XSLT 指令碼的其他範例，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。  
  
## <a name="inline-xslt-call-templates"></a>內嵌 XSLT 呼叫範本  
 與內嵌 XSLT 指令碼類似，內嵌 XSLT 呼叫範本必須直接連接到目的節點。 不過，內嵌 XSLT 呼叫範本可能使用來源結構描述與其他運算質的連結。  
  
 呼叫範本還負責建立目的節點及其任何子結構。  
  
 串連兩個項目的範例 XSLT 呼叫範本會出現在**輸入指令碼**緩衝處理，當您選取**內嵌 XSLT 呼叫範本**中**選取指令碼類型**在下拉式清單。  
  
 如需內嵌 XSLT 呼叫範本的其他範例，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。  
  
## <a name="see-also"></a>另請參閱  
 [指令碼處理運算質](../core/scripting-functoid.md)   
 [使用外部組件指令碼](../core/scripting-using-external-assemblies.md)   
 [使用內嵌 C#、 JScript.NET 和 Visual Basic.NET 指令碼](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)   
 [如何新增指令碼運算質至對應](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)