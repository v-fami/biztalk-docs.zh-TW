---
title: 工作清單中的建置錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- building, errors
- errors, building
ms.assetid: 05b36511-3031-4e13-ac2f-bfdbec0f48cb
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aeef8ac3defc17f4c9bf0fbddedf6d389a1263e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967220"
---
# <a name="build-errors-in-the-task-list"></a>建置工作清單中的錯誤
當您建置專案或解決方案時，結果會出現在 [輸出] 視窗中，至於個別錯誤和警告則會出現在工作清單中。  
  
 錯誤和警告會出現在工作清單中。 您可以按兩下該錯誤，即會將焦點套用到未正確設定的物件。  
  
> [!NOTE]
>  當您建置時，編譯器不會驗證 XPaths。 請謹慎使用有效的 XPath 語法。  
  
## <a name="insufficient-configuration-action"></a>動作組態不完整  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!CAUTION]
>  雖然「協調流程設計師」會盡可能提供組態不完整警告，不過，並不能保證您的協調流程可以在缺少這類警告的情況下正確編譯。  
  
## <a name="compiler-asks-if-you-are-missing-an-assembly-reference"></a>編譯器會詢問您是否遺漏了組件參照  
  
### <a name="problem"></a>問題  
 編譯協調流程時，您收到錯誤訊息，其中附帶了一個問題「是否遺漏組件參照?」 兩種常見的訊息為：  
  
-   命名空間 'Y' 中沒有型別或命名空間名稱 'X' (您是否遺漏了組件參考?)  
  
-   識別項 'X' 不存在於 'Y' 中; 是否遺漏組件參照?  
  
### <a name="cause"></a>原因  
 這項錯誤可能是由下列任何一項所造成：  
  
-   您的專案未參考一或多個必要的組件。  
  
-   您專案中的對應或其他物件類型與專案同名。  
  
-   您的專案使用以 XML 結構描述定義語言 (XSD) 為基礎的 Partner Interface Process (PIP) 結構描述，並且在名為 System 的子資料夾中包含了 XSD 結構描述。  
  
-   您專案中使用的某個全域屬性，其命名空間是目前專案命名空間的子集。 例如，在包含於專案 "Accounts.FILE" 內的協調流程中，使用「全域屬性」命名空間 "File.ReceivedFileName"。  
  
### <a name="resolution"></a>解決方案  
 視問題的原因而定，解決方式可以是下列任何一種：  
  
-   將專案所需組件的遺漏參考加入。  
  
-   將對應或其他物件的名稱變更為專案名稱以外的名稱。 這通常可以透過物件的屬性頁來完成 (例如，[對應] 屬性頁包含 [名稱] 屬性)。  
  
-   在 Visual Studio 中變更結構描述的命名空間。 若要這樣做使用 Visual Studio，請按一下**顯示所有檔案**上**專案**功能表，然後展開**系統**方案總管 中的節點。 按一下每個檔案系統資料夾及任何子資料夾，並因此的任何變更命名空間中的項目 [屬性] 視窗出現**系統**部分都變成 _**系統**。 例如，變更**MyProject.System.SubFolder**命名空間加入**MyProject._System.Subfolder**命名空間。 如需有關此問題，請參閱知識庫文章[916649](http://support.microsoft.com/?kbid=916649)。  
  
-   從專案中移除衝突的「全域屬性」命名空間。  
  
## <a name="you-receive-a-message-has-not-been-initialized-in-construct-statement-error-when-building-your-project"></a>當您建置專案時，收到錯誤：在建構陳述式中尚未初始化訊息  
  
### <a name="problem"></a>問題  
 當您編譯 BizTalk 應用程式時，收到錯誤「在建構陳述式中尚未初始化訊息」。  
  
### <a name="cause"></a>原因  
 建構訊息時，您指定所有的訊息變數， 然後對訊息或其部分進行指派。 如果特定訊息指派的組件會包含在個別**建構訊息**圖形，您可能會收到初始化錯誤訊息。  
  
### <a name="resolution"></a>解決方案  
 若要解決這個問題，請確定您在同一個包含所有組件的特定訊息指派**建構訊息**圖形。 如需相關的支援問題，請參閱知識庫文章[870606](http://support.microsoft.com/?kbid=870606)。  
  
 您也可以藉由建立您的訊息中解決此行為**建構**圖形，才能使用它在執行個體**運算式**圖形。 例如，下列程式碼會造成錯誤如果放在**運算式**圖形：  
  
```  
XMLDOM = new System.Xml.XmlDocument();  
POAckMsg = XMLDOM;  
```  
  
 若要修正，建立在 XMLDOM 執行個體**建構**圖形，然後再進行指派，在下游**運算式**圖形。  
  
## <a name="you-receive-a-use-of-unconstructed-message-error-when-building-your-project"></a>當您建置專案時，收到錯誤：使用未建構的訊息  
  
### <a name="problem"></a>問題  
 當您編譯 BizTalk 專案時，您會收到錯誤 「 使用未建構的訊息 '\<訊息\>' 」。  
  
### <a name="cause"></a>原因  
 當使用未建構的訊息時，就會發生此錯誤**傳送**圖形。  
  
### <a name="resolution"></a>解決方案  
 若要解決此問題，請加入**建構訊息**圖形至協調流程。 包含**建構訊息**圖形之前**傳送**繫結至 Web 服務的圖形。  
  
 如需有關此錯誤與 Web 服務，請參閱知識庫文章[921043](http://support.microsoft.com/?kbid=921043)。  
  
## <a name="setting-a-transaction-level-for-a-scope-results-in-an-error"></a>設定範圍的交易層級會產生錯誤  
  
### <a name="problem"></a>問題  
 在協調流程中設定範圍或其他支援交易之實體的交易類型之後，看到錯誤「非交易式的協調流程不能包含任何其他交易」。  
  
### <a name="cause"></a>原因  
 如果協調流程本身的交易類型為「無」，當您嘗試在協調流程中，將範圍 (或其他實體) 的交易類型設定為「不可部分完成」或「長時間執行」，就會發生這個錯誤。  
  
### <a name="resolution"></a>解決方案  
 請確定您的協調流程和構成物件的交易類型設定為相容。  
  
## <a name="project-build-results-in-the-error-you-must-specify-at-least-one-already-initialized-correlation-set-for-a-non-activation-receive-that-is-on-a-non-selfcorrelating-port"></a>建置專案時，發生錯誤：您必須為位於非自我相互關聯連接埠上的非啟動接收，至少指定一個已經初始化的相互關聯集合  
  
### <a name="problem"></a>問題  
 當您編譯 BizTalk 專案時，看到錯誤「您必須為位於非自我相互關聯連接埠上的非啟動接收，至少指定一個已經初始化的相互關聯集合」。  
  
### <a name="cause"></a>原因  
 如果沒有啟動協調流程，會發生此錯誤**接收**圖形 (Activate = true) 或沒有啟動**接收**圖形，且不直接由另一個協調流程呼叫。  
  
### <a name="resolution"></a>解決方案  
 如果您的協調流程不由另一個協調流程呼叫，您必須設定其中一種**接收**圖形，來為啟動接收。 如需有關設定**接收**圖形，包括連結的相互關聯，請參閱[如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md)。  
  
## <a name="you-receive-the-error-assembly-generation-failed----referenced-assembly-assembly-does-not-have-a-strong-name-when-building-your-solution"></a>您會收到錯誤 「 組件產生失敗--參考的組件 '\<組件\>' 沒有強式名稱 」 您建置方案時  
  
### <a name="problem"></a>問題  
 您會收到錯誤 「 組件產生失敗--參考的組件 '\<組件\>' 沒有強式名稱 」 時，建置您的方案含有協調流程。  
  
### <a name="cause"></a>原因  
 如果在協調流程中使用來自未簽署的參考組件的類型，就會發生這個問題。  
  
### <a name="resolution"></a>解決方案  
 將強式名稱套用至參考組件。 如果是可以重新編譯的自訂組件，請使用強式名稱工具建立 .snk (金鑰) 檔案，然後在專案的組件屬性中參考該金鑰檔案。 如需有關強式命名組件的詳細資訊，請參閱[如何設定強式名稱組件金鑰檔案](../core/how-to-configure-a-strong-name-assembly-key-file.md)。  
  
## <a name="the-error-failed-to-add-resources-change-requests-failed-for-some-resources-occurs-when-deploying-an-orchestration"></a>部署協調流程時，發生錯誤：無法新增資源。 某些資源的變更要求失敗。  
  
### <a name="problem"></a>問題  
 部署協調流程時，顯示了類似下列的錯誤，協調流程部署於是失敗：  
  
```  
Failed to add resource(s). Change requests failed for some resources. BizTalkAssemblyResourceManager failed to complete end type change request. Object reference not set to an instance of an object.  
```  
  
### <a name="cause"></a>原因  
 如果協調流程包含任何使用 C# 關鍵字的物件，就會發生這個錯誤。  
  
### <a name="resolution"></a>解決方案  
 從協調流程中移除任何 C# 關鍵字。 如需 C# 關鍵字的清單，請參閱[http://go.microsoft.com/fwlink/?LinkId=74346](http://go.microsoft.com/fwlink/?LinkId=74346)。  
  
## <a name="you-receive-an-invalid-property-value-error-when-compiling-your-orchestration"></a>當您編譯協調流程時，收到錯誤：無效的屬性值  
  
### <a name="problem"></a>問題  
 當您建置協調流程時，看到錯誤對話方塊顯示「無效的屬性值」。  
  
### <a name="cause"></a>原因  
 方案中的一或多個物件與另一個物件的名稱相同。 例如，訊息名稱與連接埠名稱相同。  
  
### <a name="resolution"></a>解決方案  
 確定方案中的每個物件都有唯一的名稱。 遵循命名慣例，即可降低發生此錯誤的風險。  
  
## <a name="see-also"></a>請參閱  
 [如何建置協調流程](../core/how-to-build-orchestrations.md)