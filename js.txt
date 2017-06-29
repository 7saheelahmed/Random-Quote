var quote;
var author;
function randomQuote() {
  $.ajax({
    url: "https://api.forismatic.com/api/1.0/",
    jsonp: "jsonp",
    dataType: "jsonp",
    data: {
      method: "getQuote",
      lang: "en",
      format: "jsonp"
    },
    success: function(q) {
      $('#quote').html('&ldquo;' + q.quoteText + '&rdquo;')
      $('#author').html("-" + q.quoteAuthor)
      quote=q.quoteText
      author=q.quoteAuthor
    }
  });
}

randomQuote();

//Click on the button to generate another random quote

$('#random').click(function() {

  randomQuote();

});
$("#tweet").on("click", function() {
  window.open("https://twitter.com/intent/tweet?text=" + '"' + quote + '"' + ' - ' + author);
});