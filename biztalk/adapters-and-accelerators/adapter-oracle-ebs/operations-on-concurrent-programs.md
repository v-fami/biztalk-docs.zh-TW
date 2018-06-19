---
title: 並行程式上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbc40e4c-d5a1-4763-9683-09a744e5b656
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bd7aae5d90c85e913c0e65a20f1d03e81c526e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218310"
---
# <a name="operations-on-concurrent-programs"></a>並行程式的作業
Oracle E-business Suite 中的並行程式當成作業[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  Oracle 應用程式特有的並行程式以及[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會提供諸如下列三種的標準作業： Get_Status、 Wait_For_Request 和 Submit_Request。 這表示如果 Oracle 應用程式有兩個並行程式，將會公開五個作業： 一個適用於每個並行程式，而三個用於標準的作業。  
  
 如需詳細資訊：  
  
-   瀏覽及搜尋並行程式，請參閱[瀏覽、 搜尋和 Oracle E-business 作業取得中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
-   如何叫用中的並行程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[叫用 Oracle E-business Suite 使用 BizTalk Server 中的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)。  
  
> [!IMPORTANT]
>  您必須設定應用程式內容中的並行程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]才能執行並行程式上的任何作業。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定以及成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 應用程式內容，以及如何設定它的相關資訊，請參閱設定應用程式內容[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
 下列各節提供有關所公開的作業資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]並行程式。  
  
##  <a name="Concurrent"></a>< Concurrent_Program_Name > 作業  
 如先前所述，將會有許多 < Concurrent_Program_Name > 作業是 Oracle 應用程式中的並行程式數目。 < Concurrent_Program_Name > 作業採用五個標準的參數： 三個複雜型別和兩個簡單類型。  
  
> [!NOTE]
>  Oracle E-business 配接器不會公開其中繼資料的並行程式，每個這些並行程式可 100 的選擇性參數。 順利叫用這些並行程式，使用者必須請參閱 Oracle E-business Suite 文件，找出需要值，並行處理程式的參數，然後將其指定。 並行程式的範例是**筆記本的匯入**(實際名稱： **GLLEZL**) 中**一般分類帳**應用程式。  
  
 **複雜型別參數**  
  
-   **SetOptions**： 可讓您設定並行程式的選項，再提交要求。 SetOptions 接受做為參數的下列選項：  
  
    -   **隱含**： 指出是否要顯示 Oracle E-business Suite 中的使用者的並行要求表單中的 並行要求。 您可以指定任何下列四個值：**否**，**是**，**錯誤**或**警告**。 指定**否**會導致在 Oracle E-business Suite 中的使用者的並行要求表單中顯示的要求。 指定**是**表示要求，可以檢視只能從系統管理員特殊權限的並行要求表單。 指定**錯誤**導致要求失敗時，才會顯示在使用者的並行要求表單中。 指定**警告**會要求顯示在使用者的並行要求表單只有當沒有警告或錯誤。  
  
    -   **受保護的**： 指出是否要將並行要求保護針對 Oracle E-business Suite 中使用並行要求表單所做的更新。 您可以指定**是**(protected) 或**否**（未受保護）。  
  
    -   **語言**： 表示的國家語言支援 (NLS) 語言。 如果未不指定任何值，它會預設為目前的語言。  
  
    -   **領域**： 指出語言領域。 如果未不指定任何值，它會預設為目前語言領域。  
  
    -   **ContinueOnFail**： 指出並行要求送出應該繼續還是擲回例外狀況，萬一**SetOptions**失敗。 您可以指定**True** （繼續） 或**False** （擲回例外狀況）。  
  
-   **SetPrintOptions**： 可讓您設定並行程式的列印選項，再提交要求。 SetPrintOptions 接受做為參數的下列選項：  
  
    -   **印表機**： 指出並行要求的輸出應該傳送位置的印表機名稱。 如果它已設定 Oracle E-business Suite 中的並行程式表單中，您無法覆寫此列印選項。  
  
    -   **樣式**： 指出用來同時並存要求輸出列印的列印樣式。 例如，您可以指定方向 (**橫向**或**縱向**)。 如果已經在 Oracle E-business Suite 中，並行程式形式設定列印樣式和**所需的樣式**選取核取方塊，您無法覆寫此列印選項。  
  
    -   **複製**： 指出要並行要求的輸出的列印的份數。  
  
    -   **SaveOutput**： 指出是否要儲存輸出檔案。 您可以指定**是**或**否**。  
  
    -   **PrintTogether**： 只適用於包含子要求這些要求。 表示子要求的輸出列印的方式。 如果您指定**Y**，所有的子要求已完成之後，才列印輸出的子要求。 如果您指定**N**，完成列印輸出的每一個子要求。  
  
    -   **ContinueOnFail**： 指出並行要求送出應該繼續還是擲回例外狀況，萬一**SetPrintOptions**失敗。 您可以指定**True** （繼續） 或**False** （擲回例外狀況）。  
  
-   **SetRepeatOptions**： 可讓您設定並行程式重複的選項，再提交要求。 **SetRepeatOptions**會做為參數的下列選項：  
  
    -   **RepeatTime**： 指出要重複並行要求的當日時間。  
  
    -   **RepeatInterval**： 這是參數時才適用**RepeatTime**是 NULL。 表示要求的 resubmissions 之間的間隔。 使用此選項，連同**RepeatUnit**指定 resubmissions 之間的時間。  
  
    -   **RepeatUnit**： 這是參數時才適用**RepeatTime**是 NULL。 時間與單位**RepeatInterval**若要指定要求的 resubmissions 之間的時間。 您可以指定**分鐘**，**小時**，**天**或**月**。  
  
    -   **RepeatType**： 這是參數時才適用**RepeatTime**是 NULL。 指出是否要在並行要求執行 「 結束 」 或 「 開始 」 同時並存要求執行作業的之後，套用將重複間隔。  
  
    -   **RepeatEndTime**： 指出停止重新提交具有並行要求的日期和時間。  
  
    -   **ContinueOnFail**： 指出並行要求送出應該繼續還是擲回例外狀況，萬一**SetRepeatOptions**。 您可以指定**True** （繼續） 或**False** （擲回例外狀況）。  
  
 **簡單的型別參數**  
  
-   **描述**： 並行要求的描述。  
  
-   **StartTime**： 表示並行的要求應該開始執行的時間。  
  
## <a name="getstatus-operation"></a>Get_Status 作業  
 標準作業 Get_Status，傳回要求階段/狀態和完成訊息的並行處理的程式。 這項作業會採用並行處理程式的要求識別碼 (**RequestID**) 做為輸入，然後傳回下列資訊：  
  
-   **階段**: FND_LOOKUPS 從 「 使用者易記的要求 」 階段。  
  
-   **狀態**: FND_LOOKUPS 的使用者易記的要求狀態。  
  
-   **DevPhase**: 「 要求 」 階段為字串，可用於程式邏輯比較。  
  
-   **DevStatus**： 要求的狀態，可用於程式邏輯比較的字串。  
  
-   **訊息**： 完成訊息，如果要求已完成。  
  
## <a name="waitforrequest-operation"></a>Wait_For_Request 作業  
 標準作業 Wait_For_Request，等候要求完成，然後傳回要求階段/狀態和完成訊息。 這項作業會採用並行處理程式的要求識別碼 (**RequestID**)，檢查之間要等候的秒數 (**間隔**)，並等候要求完成 （秒鐘的時間上限**MaxWait**) 做為輸入參數，然後傳回如同 Get_Status 作業相同的資訊。  
  
## <a name="submitrequest-operation"></a>Submit_Request 作業  
 標準作業 Submit_Request，提交並行管理員所處理的並行要求。 如果要求成功地完成此操作會傳回並行要求識別碼。 否則，它會傳回"0"。  
  
 Submit_Request 作業採用六個標準的參數： 三個每個複雜類型的簡單類型。 除了這些參數，它也會使用並行程式的引數為字串的陣列。  
  
 **複雜型別參數**  
  
 Submit_Request 作業會採用**SetOptions**， **SetPrintOptions**，和**SetRepeatOptions**做為輸入參數。 如需這些參數的詳細資訊，請參閱[ &lt;Concurrent_Program_Name&gt;作業](#Concurrent)稍早在這一節。  
  
 **簡單的型別參數**  
  
-   **程式**： 提交要求的並行程式簡短名稱。  
  
-   **描述**： 並行要求的描述。  
  
-   **StartTime**： 並行要求應該開始執行的時間。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)