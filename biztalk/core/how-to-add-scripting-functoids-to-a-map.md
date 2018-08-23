---
title: 如何新增指令碼處理運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.functiod.script
ms.assetid: eb96814a-b3fb-48f6-a947-ab595a270faa
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e983564b448ef27323879c6db15ccc232d032d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019136"
---
# <a name="how-to-add-scripting-functoids-to-a-map"></a>如何新增指令碼處理運算質至對應
**指令碼處理**運算質可讓您使用自訂指令碼或程式碼在執行階段來執行無法使用的功能。 例如，您可以在執行階段呼叫 COM 物件使用**指令碼處理**運算質和撰寫您自己自訂的指令碼。  
  
 如需概念性資訊**Scripting**運算質，請參閱[指令碼處理運算質](../core/scripting-functoid.md)。  
  
### <a name="to-add-the-scripting-functoid-to-a-map-and-configure-it"></a>新增指令碼處理運算質至對應並設定  
  
1. 具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 **進階運算質**来選取該運算質類別索引標籤。  
  
    顯示所選類別中的進階運算質清單。  
  
2. 拖曳**Scripting**運算質![](../core/media/bts-tls-scripting.gif "bts_tls_scripting")從工具箱拖曳至格線頁上的適當位置。  
  
   > [!NOTE]
   >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
   > [!NOTE]
   >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3. 選取 **指令碼處理**您剛新增至顯示的格線頁的運算質。  
  
4. 在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性] 視窗中，按一下省略符號 (**...**) 按鈕相關聯**指令碼**屬性。  
  
   > [!NOTE]
   >  或者，您可以在此運算質，以滑鼠右鍵按一下，然後按一下**設定運算質指令碼**操作功能表中。 **設定指令碼處理運算質**對話方塊會顯示**指令碼運算質組態**選取的索引標籤。  
  
5. 在 **設定指令碼處理運算質**對話方塊的 **選取指令碼類型**下拉式清單中，選取您的指令碼的類型。  
  
   > [!NOTE]
   >  視您所選的指令碼類型而定，將會啟用和停用其餘對話方塊欄位的不同子集。  
  
6. 如果您選取**外部組件**做為指令碼類型，使用**指令碼組件**，**指令碼類別**，以及**指令碼方法**下拉式清單清單中的，依序選取組件、 類別和方法，分別將與這個**指令碼處理**運算質。  
  
   > [!WARNING]
   >  外部組件中的程式碼必須是安全執行緒。 在負荷條件下，對應的多個執行個體可能會同時執行。  
  
   > [!NOTE]
   >  選取組件之後,**指令碼類別**下拉式清單將填入該組件中的類別。 同樣地，之後您已選取類別**指令碼方法**下拉式清單將填入該類別中的方法。  
  
   > [!NOTE]
   >  **內嵌指令碼**文字方塊中已停用，當您選取**外部組件**的指令碼類型。  
  
    如果您選取的項目以外**外部組件**做為指令碼類型 （其中一個內嵌選擇），使用**內嵌指令碼**文字方塊中輸入您的指令碼中您選取的語言。  
  
   > [!NOTE]
   >  內嵌語言選擇**指令碼處理**運算質包含 C#.NET、 jscript.net、 Visual Basic.NET、 XSLT 和 XSLT 呼叫範本。  
  
    使用 C# 的指令碼不允許 "using" 陳述式。 如果指令碼需要使用任何特殊 .Net 類別，則您應該將對應的組件及其相依組件新增至 BizTalk 專案的 [參考]，且指令碼應該使用完整名稱。 如果您撰寫指令碼來執行區分文化特性的小寫轉換，應該撰寫如下的對應程式碼片段。 所有支援的指令碼語言都受到類似的限制。  
  
   ```  
   string x = y.ToLower(System.Globalization.CultureInfo.CurrentCulture);  
   ```  
  
    在指令碼中，若要使用任何組件中的類別，請確定您將對應的組件及其相依組件新增至您的對應所在之 BizTalk 專案中的 [參考]。  
  
   > [!NOTE]
   >  您可以建立自訂指令碼中直接**內嵌指令碼**文字方塊中，或者您可以建立您的指令碼中其他位置，並將它貼到**內嵌指令碼**文字方塊。  
  
   > [!NOTE]
   >  **指令碼組件**，**指令碼類別**，並**指令碼方法**下拉式清單會停用，當您選取其中一個內嵌選擇 (項目以外**外部組件**) 的指令碼類型。  
  
   > [!IMPORTANT]
   >  若您建立包含多個函式的指令碼，則第一個函式將被視為主要函式；只有在執行主要函式時，才會呼叫其他函式。  
  
    按一下 [確定] 。  
  
7. 若外部組件中的指令碼或關聯的方法需要輸入參數，則如同您建立基本運算質一樣地建立適當的輸入連結數目與類型。  
  
8. 在大部分情況下，您**指令碼處理**運算質將產生輸出值，用於填入目的結構描述中的欄位，或做為另一個運算質的輸入，在大部分相同方式基本運算質執行。  
  
## <a name="see-also"></a>另請參閱  
 [將進階運算質新增至對應](../core/adding-advanced-functoids-to-a-map.md)